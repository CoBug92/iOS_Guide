## Какие есть нюансы при использовании `Core Data в разных потоках`? Как `синхронизировать данные между потоками`(Как синхронизировать контекст)? Синхронизация разных типов NSManagedObjectContext (получение и изменение данных в child контекстах)?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

<br/><br/>
#### Надо перечитать и переработать
<br/><br/><br/>

`NSManagedObjectContext` не потокозащищенный:

В iOS 6.0 появились типы `NSManagedObjectContext`:
1. `NSMainQueueConcurrencyType` – доступен исключительно с главного потока.
2. `NSPrivateQueueConcurrencyType` – работает на фоновом потоке.
3. `NSConfinementConcurrencyType` – работает на том потоке, на котором создали.

```Objective-C
dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{
        // Создание NSManagedObjectModel
        // Создаем NSPersistentStoreCoordinator
        // Добавляем к NSPersistentStoreCoordinator хранилище, именно на этой операции приложение может висеть очень долго

        // Создание контекстов

 Создаем родительский контекст, который будет иметь тип NSPrivateQueueConcurrencyType.

/*
        _daddyManagedObjectContext = [[NSManagedObjectContext alloc]  initWithConcurrencyType:NSPrivateQueueConcurrencyType];
    [_daddyManagedObjectContext setPersistentStoreCoordinator:psc];
    // Далее в главном потоке инициализируем main-thread context, он будет доступен пользователям
    dispatch_async(dispatch_get_main_queue(), ^{
        _defaultManagedObjectContext = [[NSManagedObjectContext alloc]  initWithConcurrencyType:NSMainQueueConcurrencyType];
        // Добавляем наш приватный контекст отцом, чтобы дочка смогла пушить все изменения
        [_defaultManagedObjectContext setParentContext:_daddyManagedObjectContext];
    });
*/
});
```

Дальше создаем `defaultManagedObjectContext` и задаем ему родителя (_daddy...)

При работе в других потоках задаем в качестве предка defaultManagedObjectContext.

Сохранение контекстов:

Осталось самое главное — сохранение. К контекстам, которые живут на бекграунд-потоках обращаться можно только через performBlock: и performBlockAndWait:. Поэтому сохранение бекграунд потока будет выглядеть следующим образом.

```Objective-C
- (void)saveContextForBGTask:(NSManagedObjectContext *)bgTaskContext {
    if (bgTaskContext.hasChanges) {
        [bgTaskContext performBlockAndWait:^{
            NSError *error = nil;
            [backgroundTaskContext save:&error];
        }];
       // Save default context
    }
}
```
После сохранения дочернего контекста необходимо сохранить родительский.

```Objective-C
- (void)saveDefaultContext:(BOOL)wait {
    if (_defaultManagedObjectContext.hasChanges) {
        [_defaultManagedObjectContext performBlockAndWait:^{
            NSError *error = nil;
            [_defaultManagedObjectContext save:&error];
        }];
    }

    // А после сохранения _defaultManagedObjectContext необходимо сохранить его родителя, то есть _daddyManagedObjectContext
    void (^saveDaddyContext) (void) = ^{
        NSError *error = nil;
        [_daddyManagedObjectContext save:&error];
    };
    if ([_daddyManagedObjectContext hasChanges]) {
        if (wait)
            [_daddyManagedObjectContext performBlockAndWait:saveDaddyContext];
        else
            [_daddyManagedObjectContext performBlock:saveDaddyContext];
    }
}
```

А вообще, лучше использовать фреймворк MagicalRecord, в котором реализована работа с потоками.
