## Что такое `KVO`? Когда его нужно использовать? Методы для обозревания объектов? Работает ли `KVO с instance переменными (полями)` объекта?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

### Что такое `KVO`?
`KVO` предоставляет механизм, который позволяет объектам получать оповещение во время изменения каких-либо из их свойств.

###  Когда его нужно использовать?

Если мы хотим, чтобы один объект выполнял какие-либо действия, во время изменения свойств другого объекта.
Например, мы имеем `PersonObject` и `BankObject`. В случае, если меняется свойство `accountBalance` в объекте `BankObject`.
Мы хотим вызывать определенный метод в `PersonObject`.

### Методы для обозревания объектов?

В нашем примере:
```Objective-C
 [bankInstance addObserver: personInstance
                froKeyPath: @"accountBalance"
                   options: NSKeyValueObservingOptionNew
                   context: NULL];
```

в `PersonObject` реализуем метод:

```Objective-C
- (void) observeValueForKeyPath: (NSString *)keyPath
                       ofObject: (id)object
                         change: (NSDictionary *)change
                        context: (void *)context {
                          // code
                        }
```

### Работает ли `KVO с instance переменными (полями)` объекта?

Да.
