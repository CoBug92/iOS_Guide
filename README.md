# Вопросы и ответы на собеседование iOS разработчика:

=======
General:
--------
- [Что такое `полиморфизм`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/OOP/Polymorphism.md)
- [Что такое `инкапсуляция`? Что такое нарушение инкапсуляции?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/OOP/Encapsulation.md)
- [Чем `абстрактный класс` отличается от `интерфейса`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/OOP/Abstract_class_vs_interface.md)
- [Что такое `SOLID` принципы?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/SOLID.md)
- [Расскажите о паттерне `MVC`. Чем отличается `пассивная` модель от `активной`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/Pattern/MVC_active_vs_passive.md)
- [Какие еще `паттерны` знаете?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/Pattern/Little_bit_about_patterns.md)
- Что такое `responder chain`?
- [Как работают `push нотификации`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/How_to_work_with_push_notification.md)

UIKit:
------
- [Цикл жизни ios-приложения](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/ios_general/app_lifecycle.md)
- Разница между свойствами `bounds и frame` объекта UIView? Понимание системы координат?
- Какие бывают `состояния` у приложения?
- Цикл жизни `UIViewController`?
- Что такое `View` (представление) и что такое `window`?
- Какого разрешение экранов iphon'ов, и в чем разница между `points (точками)` и `пикселями (pixels)`?
- [Что такое `responder chain` (цепочка обязанностей, `паттерн chain of responsibility`, на примере UI компонентов iOS ), `becomeFirstResponder`.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/uikit/responder_chain.md)
- Что означают `IBOutlet` и `IBAction`, для чего они нужны, и что значат для препроцессора?
- Как работает `UITableView`?
- Как многопоточность работает с `UIKit`?
- Что можно сделать если клавиатура при появлении скрывает важную часть интерфейса?
- Почему мы должны `релизить IBOutlet'ты` во viewDidUnload?
- Что такое `awakeFromNeeb`, в чем разница между `xib и nib` файлами?
- Иерархия наследования UIButton.


Networking:
----------
- Преимущества и недостатки `синхронного и асинхронного` соединения?
- [Что означает `http, tcp`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/networking/http_tcp.md)
- [Какие различия между `HEAD, GET, POST, PUT`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/networking/difference_between_head_get_post_put.md)
- Как загрузить что-то из интернета? В чем разница между `синхронными и асинхронными запросами`? Небольшое задание. Опишите как загрузить изображение из интернета и отобразить его в ImageView — все это должно происходить после нажатия кнопки.
- [Архитектура REST](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/networking/rest.md)

Multithreading:
---------------
- [Что такое `deadlock`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/deadlock.md)
- [Что такое `livelock`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/livelock.md)
- [Что такое `семафор (semafor)`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/semaphore.md)
- [Что такое `мьютекс (mutex)`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/mutex.md)
- `Асинхронность` vs `многопоточность`. Чем отличаются?
- [Что такое `состояние гонки`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/race_condition.md)
- [Какие технологии в iOS возможно использовать для работы с потоками. Преимущества и недостатки.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/another_thread_technology.md)
- Как запустить поток? Что первым нужно сделать при запуске потока? (NSAutoreleasePool - пул автоосвобождения) Что такое runLoop, кодга он используется? (timers, nsurlconnection …)
- [Чем отличается `dispatch_async от dispatch_sync`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/dispatch_sync_vs_async.md)
- Для чего при разработке под iOS использовать `POSIX-потоки`? `pthread_create(&thread, NULL, startTimer, (void *)t);`
- А чем реально `POSIX-потоки` лучше чем `GCD или NSOperationQueue вместе с NSOperation`? Приходилось ри реально использовать POSIX и как в этом были прюсы? Реально, просто интересно…
 `Use POSIX calls if cross-platform portability is required. If you are writing networking code that runs exclusively in OS X and iOS, you should generally avoid POSIX networking calls, because they are harder to work with than higher-level APIs. However, if you are writing networking code that must be shared with other platforms, you can use the POSIX networking APIs so that you can use the same code everywhere. `

Базы данных, CoreData:
----------------------
- Составить SQL запрос на выборку всех проектов  на которых сидит девелопер с
id ==3. (`Developers:id,name; Projects:id,name; Developers&Projects:project_id,developer_id`)?
- Зачем нужно делать `двустороннии связи` в таблицах?

- [Что такое `Core Data`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/coredata/coredata.md)
- [В каких случаях лучше использовать `SQLite`, а в каких `Core Data`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/coredata/sqlite_vs_coredata.md)
- ~~Что такое `контекст (Managed object context)`? Как происходят `изменения в NSManagedObjectContext`?~~
- ~~Что такое `Persistent store coordinator`? Зачем нужен `NSPersistentStoreCoordinator`?~~
- [Какие есть нюансы при использовании `Core Data в разных потоках`? Как `синхронизировать данные между потоками`(Как синхронизировать контекст)? Синхронизация разных типов NSManagedObjectContext (получение и изменение данных в child контекстах)?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/coredata/coredata_vs_threads.md)

- [Использовали ли `NSFetchedResultsController`? Почему?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/coredata/nsfetchresultcontroller.md)
- Что такое `Fault` и зачем он нужен?
- Что таке `Fetched Property` и особенности работы с ним по сравнению с обычной связью?
- Как использовать `СoreData` совместно с `многопоточностью`?
- Что такое `NSManagedObjectId`? Можем ли мы сохранить его на потом если приложение закроется?
- Какие `типы хранилищ` поддерживает CoreData?
- Что такое `ленивая загрузка (lazy loading)`? Что ее связывает с CoreData? Опишите ситуация когда она может быть полезной?

CoreAnimation, CoreGraphics:
----------------------------
- Чем отличается `UIView от CALayer`?
- Какие типы `CALayer` есть?
- Чем отличается `UIView based Animation от Core Animation`?
- Тайминги в `CoreAnimation`?
- Что такое `backing store`?
- Чем отличаются `аффинные преобразования от трехмерных`?
- Нужно ли `ретейнить (посылать сообщение retain)` делегат для `CAAnimation`?

Algorithms:
-----------
- Напишите код, который `разворачивает строку на С++`. (переставить символы в строке в обратном порядке)?
- Поменять местами a и b не используя промежуточную переменную?
- Написать функцию вычисления n-го числа последовательности фебоначи. (если решить через рекурсию, спросят чем опасно такое решение)?
- Решить задачку о массиве: дан массив из 1001 элемента в котором присутсвуют все числа от 1 до 1000 и одно повторяется дважды, узнать какое, если к каждому элементу можно обратиться только 1 раз?
- Как из строки вытащить подстроку?

Logical:
--------
Есть 4 человека, каждый проходит мост за 1, 2, 5, и 10 минут соответственно. Через мост они могут переходить только парами, держась за руку и только с фонариком. Притом один должен вернуться обратно и передать фонарик. Необходимо переправить всех за 17 мин на другую сторону. Задача решаема.

[Решение](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/logical/bridge.md)
























Objective-C, Foundation:
------------------------

- [Реализация `синглтона (Singleton)` в `ARC` и в `non-ARC`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/Pattern/Singleton_arc_non_arc.md)
- [Что такое UINavigationController?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/uinavigationcontroller.md)

- [Опишите `основные понятия ОО программирования` в терминах Objective-C (`интерфейс, реализация, свойства, протоколы,` иa т.д)](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/base_oop_term_per_objc.md)
- [Что такое назначеный `инициализатор (designated initializer`), напишите любой элементарный инициализатор, почему он так выглядит? (имеется ввиду `if (self  = [super ...])`)?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/designated_initializer.md)
- [Суть `рантайма (Runtime), отправление сообщения`](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/runtime.md)
- [Как добавить свойство в существующий объект с закрытой реализацией через runtime?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/add_property_in_runtime.md)
- Объявление `свойств (property)` `(retain, assign, nonatomic, readonly, copy)`. С подвохом: вопрос о несуществующем параметре `atomic`, что он означает? Как правильно реализовать сетер для свойства с параметром retain? Вопрос о циклах в графах владения, и почему свойства delegate (предоставляющие доступ к делегату) обычно задаются как `assign`?
- [Разница между NSObject и id?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/nsobject_vs_id.md)
- В чем разница между `точечной нотацией` и использованием квадратных скобок? Что происходит когода мы пытаемся вызвать метод у nil указателя?
- [Разница между `nil` и `Nil`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/nil_Nil_NSNull.md)
- [Что такое `селектор (selector)`?Как его вызвать? как отложить вызов селектора?Что делать если селектор имеет много параметров? `(NSInvocation)`](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/selector.md)
- Как запустить селектор во второстепенном `(фоновом) потоке`?
- Как запустить `поток`? Что первым нужно сделать при запуске `потока`? `(NSAutoreleasePool)` Что такое `runLoop`, кодга он используется? `(timers, nsurlconnection ...)`
- [Что такое `делегат (delegate)`? как его создать и использовать?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/delegate.md)
- Как представлены `структуры C` (CGRect, CGSize, CGPoint) в Objective-C?
- Чем объект Objective-c отличается от структуры С, что такое структура в С.
- [Какие существуют `root классы` в iOS? Для чего нужны `root классы`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/root_classes.md)
- Корневые классы: NSObject, NSProxy? Как работает proxy? Как эмитировать множественное наследование?
- [`Тип id`. Что случится во время компиляции если мы посылаем сообщение объекту `типа id`? ](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/send_message_to_id.md)
- Что случится во время выполнения если этот метод существует? Что произойдет здесь (компиляция  + время выполнения): `NSString *s = [NSNumber numberWithInt:3]; int i = [s intValue];`
- [Что такое `указатель isa`? Для чего он нужен?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/isa.md)
- [Что происходит с методом после того, как он не нашелся в объекте класса, которому его вызвали?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/not_find_method_in_object.md)
- Цепочка ответсвенности, что происходит с методом после того как он не нашелся в объекте класса, которому его вызвали (в сторону forwardInvocation:)?
- [Чем `категория` отличается от `расширения` (extension, наименованная категория)? `категория vs extension`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/category_vs_extention.md)
- [Можно ли добавить `ivar` в категорию?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/ivar_in_category.md)
- [Когда лучше использовать `категорию`, а когда `наследование`? `категория vs наследование`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/category_vs_inheritance.md)
- Что такое `notifications (уведомления)`? как мы должны их использовать?
- [Какая разница между использование `делегатов (delegation)` и `нотификейшенов (notification)`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/delegate_vs_notification.md)
- [В чем разница между `NSArray и NSMutableArray`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/nsarray_nsmutablearray.md)
- [Чем отличается `NSSet от NSArray`? Какие `операции` происходят быстро в `NSSet` и какие в `NSArray`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/NSSet_NSArray.md)
- [Как получить текущую координату?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/how_get_current_coordinate.md)
- [Формальный и неформальный (informal) протокол?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/formal_vs_informal_protocol.md)
- Протоколы (protocols): основные отличия между c#/java интерфейсами и Objective-C протоколами. Что делать в случае если класс не реализует какой-то метод из протокола?
- [Есть ли `приватные и защищенные` методы в Objective-C?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/private_and_protected_methods.md)
- [Что такое `быстрое перечисление (fast enumeration)`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/fast_enumeration.md)
- Как имитировать `множественное наследование`?
- [Что такое `KVO`? Когда его нужно использовать? Методы для обозревания объектов? Работает ли `KVO с instance переменными (полями)` объекта?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/kvo.md)
- Что такое `KVC`? Когда его нужно использовать?
- Как удалить объект в ходе итерации по циклу?
- [Что такое `Run Loop`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/run_loop.md)
- Как лучше всего загрузить `UIImage c диска(с кеша)`?
- Какой контент лучше хранить в `Documents`, а какой в `Cache`?
- Как связаны `NSRunLoop и NSAutoreleasePool` на пальцах?
- [Что такое autorelease?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/autorelease.md)
- Почему нам не следует вызывать `instance методы в методе initialize`,?
- `NSCoding, archiving`
- Протокол `NSCopying`, почему мы не можем просто использовать любой собственный объект в качестве ключа в словарях (NSDictionary) , что нужно сделать чтобы решить эту проблему? (разница между глубоким и поверхностным копированием)
- [Безымянные методы.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/noname_methods.md)
- [Квадратные скобки для доступа к элементам массива или словаря можно использовать и со своими объектами.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/new_methods.md)
- [Неявные property](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/implicit_property.md)
- [Распечатать текущий autorelease pool.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/print_autoreleasepool.md)
- [Доступ к публичным ivar-ам как в структурах.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/ivar_access.md)
- [Использование instancetype.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/instancetype.md)
- [Проксирование: forwardingTargetForSelector: и forwardInvocation:](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/proxing.md)
- [NSFastEnumeration](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/objective_c/nsfastenumaration.md)

Memory Management:
------------------
- [Как происходит `ручное управление памятью - MRC` в iOS?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/mrc.md)
- `autorelease vs release`?
- [Что такое autorelease pool?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/autorelease_pool.md)
- [Что означает `ARC`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/arc.md)
- [Что делать, если проект написан с использованием ARC, а нужно использовать классы сторонней библиотеки написанной без ARC?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/how_use_non_arc_libs.md)
- [`Weak vs assign`, `strong vs copy`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/weak_vs_assign__strong_vs_copy.md)
- [`Atomic vs nonatomic`. Чем отличаются? ](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/atomic_vs_nonatomic.md)
- Как вручную переопределить atomic/nonatomic сеттер в не ARC коде?
- Зачем все свойства ссылающиеся на делегаты `strong/retain`. :)))
- Что такое `autorelease pool`?
- ~~Как можно заимплементировать `autorelease pool на с++`?~~
- Если я вызову `performSelector:withObject:afterDelay:` - объекту пошлется сообщение retain?
- [Как происходит обработка `memory warning`(предупреждение о малом  количестве памяти)?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/memory_warning.md)
- Зависит ли обработка от версии iOS, как мы должны их обрабатывать?
- Напишите простую реализацию `NSAutoreleasePoll` на Objective-C
- Когда нужно использовать метод `retainCount` (никогда, почему?) Объясните что такое `подсчет ссылок (retain count`)?
- Темы управления памятью, такие как владение `retain/release/autorelease`.
- Что случится если вы добавите только что созданный объект в `Mutable Array`, и пошлете ему сообщение `release`? Что случится если послать сообщение `release` массиву? Что случится если вы удалите объект из массива и попытаетесь его использовать?
- С подвохом: `сборщик мусора` для iPhone.
- [Нужно ли `ретейнить` (посылать сообщение retain) `делегаты`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/retain_delegate.md)
- Для чего используется класс `NSCoder`?
- Опишите правильный способ управленя памятью выделяемой под `Outlet'ы`?
- Реализуйте следующие методы: `retain, release, autorelease`?
- [Ручное выделение памяти под объект без alloc.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/memory_managment/manual_allocation.md)




Code Puzzels:
-------------
- [Что не так с этим кодом? Зачем нужны `инициализаторы`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/code_puzzles/code_puzzles_2.md)

```objective-c
[[[SomeClass alloc] init] init];
```

- Сработает ли `таймер`? Почему?

```objc
void startTimer(void *threadId)
{
   [NSTimer  scheduleTimerWithTimeInterval:10.0f
      target:aTarget
          selector:@selector(tick: )
          userInfo:nil
           repeats:NO];
}
pthread_create(&thread, NULL, startTimer, (void *)t);
```


- [Какой метод вызовется: класса A или класса B? Как надо изменить код, чтобы вызвался метод класса A?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/code_puzzles/method_classA_and_classB.md)

```objective-c
@interface A : NSObject
- (void)someMethod;
@end

@implementation A
- (void)someMethod
{
    NSLog(@"This is class A");
}
@end

@interface B : A
@end

@implementation B
- (void)someMethod
{
    NSLog(@"This is class B");
}
@end

@interface C : NSObject
@end

@implementation C
- (void)method
{
    A *a = [B new];
    [a someMethod];
}
```

- В каких случаях лучше использовать `strong`, а в каких `copy` для NSString? Почему?

```objc
@property (nonatomic, strong) NSString *someString;
@property (nonatomic, copy) NSString *anotherString;
```

- Что выведется в консоль? Почему?

```objc
- (BOOL)objectsCount
{
    NSMutableArray *array = [NSMutableArray new];
    for (NSInteger i = 0; i < 1024; i++)
    {
        [array addObject:[NSNumber numberWithInt:i]];
    }
    return array.count;
}

- (void)someMethod
{
    if ([self objectsCount])
    {
        NSLog(@"has objects");
    }
    else
    {
        NSLog(@"no objects");
    }
}
```

- [Выведется ли в дебагер «Hello world»? Почему?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/deadlock_example_1.md)

```Objective-C
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    dispatch_sync(dispatch_get_main_queue(), ^{
        NSLog(@"Hello world");
    });

   /* Another implementation */
   return YES;
}
```

- [Что выведется в консоль?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/code_puzzles/GCD_example_1.md)

```Objective-C
 dispatch_async(dispatch_get_main_queue(), ^
    {
        NSLog(@"A %d", [object retainCount]);
        dispatch_async(dispatch_get_main_queue(), ^
        {
            NSLog(@"B %d", [object retainCount]);
        });
        NSLog(@"C %d", [object retainCount]);
    });
    NSLog(@"D %d", [object retainCount]);
```

- [Что произойдет при исполнении следующего кода?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/code_puzzles/code_puzzles_1.md)
```Objective-C
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];
```



Swift:
-------------
- [Weak vs unowned](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/swift/weak_vs_unowned.md)
- [escaping in closures](http://stackoverflow.com/questions/39063499/updating-closures-to-swift-3-escaping)



## Контакты для связи:
* skype: torlopov.andrey
* email: [torlopov.andrey@gmail.com](mailto:torlopov.andrey@gmail.com)
* github: [https://github.com/Torlopov-Andrey](https://github.com/Torlopov-Andrey)
