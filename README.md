# Вопросы и ответы для собеседования на позицию iOS разработчика:

=======
General:
--------
- [Что такое `полиморфизм`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/OOP/Polymorphism.md)
- [Что такое `инкапсуляция`? Что такое нарушение инкапсуляции?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/OOP/Encapsulation.md)
- [Чем `абстрактный класс` отличается от `интерфейса`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/OOP/Abstract_class_vs_interface.md)
- [Что такое `SOLID` принципы?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/SOLID.md)
- [Расскажите о паттерне `MVC`. Чем отличается `пассивная` модель от `активной`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/Pattern/MVC_active_vs_passive.md)
- [Какие еще `паттерны` знаете?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/General/Pattern/Little_bit_about_patterns.md)

UIKit:
------
- [Цикл жизни ios-приложения. Какие бывают `состояния` у приложения?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/App_lifecycle.md)
- [Разница между свойствами `bounds и frame` объекта UIView? Понимание системы координат?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/Frame_vs_Bounds.md)
- [Цикл жизни `UIViewController`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/UIViewController_lifecycle.md)
- Что такое `View` (представление) и что такое `window`?
- [Какого разрешение экранов iphon'ов, и в чем разница между `points (точками)` и `пикселями (pixels)`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/Size_of_iPhone_and_different_between_points_and_pixels.md)
- [Что означают `IBOutlet` и `IBAction`, для чего они нужны, и что значат для препроцессора?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/IBOutlet_vs_IBAction.md)
- [Как работает `UITableView`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/Use_UITableView.md)
- [Как многопоточность работает с `UIKit`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/Multithreading_with_UI/Multithreading_with_UI.md)
- Что можно сделать если клавиатура при появлении скрывает важную часть интерфейса?
- Почему мы должны `релизить IBOutlet'ты` во viewDidUnload?
- Что такое `awakeFromNeeb`, в чем разница между `xib и nib` файлами?
- Иерархия наследования UIButton.
- [Что такое `responder chain`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/Responder_chain.md)
- [Как работают `push нотификации`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/UIKit/How_to_work_with_push_notification.md)


Multithreading:
---------------
- [Что такое `состояние гонки`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/Multithreading/Race_condition.md)
- [Что такое `deadlock`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/Multithreading/Deadlock.md)
- [Что такое `livelock`?](https://github.com/CoBug92/Interview_iOS/blob/master/Answers/Multithreading/Livelock.md)
- [Что такое `семафор (semafor)`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/semaphore.md)
- [Что такое `мьютекс (mutex)`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/mutex.md)
- `Асинхронность` vs `многопоточность`. Чем отличаются?
- [Какие технологии в iOS возможно использовать для работы с потоками. Преимущества и недостатки.](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/another_thread_technology.md)
- Как запустить поток? Что первым нужно сделать при запуске потока? (NSAutoreleasePool - пул автоосвобождения) Что такое runLoop, кодга он используется? (timers, nsurlconnection …)
- [Чем отличается `dispatch_async от dispatch_sync`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/dispatch_sync_vs_async.md)
- Для чего при разработке под iOS использовать `POSIX-потоки`? `pthread_create(&thread, NULL, startTimer, (void *)t);`
- А чем реально `POSIX-потоки` лучше чем `GCD или NSOperationQueue вместе с NSOperation`? Приходилось ри реально использовать POSIX и как в этом были прюсы? Реально, просто интересно…
 `Use POSIX calls if cross-platform portability is required. If you are writing networking code that runs exclusively in OS X and iOS, you should generally avoid POSIX networking calls, because they are harder to work with than higher-level APIs. However, if you are writing networking code that must be shared with other platforms, you can use the POSIX networking APIs so that you can use the same code everywhere. `


Networking:
----------
- Преимущества и недостатки `синхронного и асинхронного` соединения?
- [Что означает `http, tcp`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/networking/http_tcp.md)
- [Какие различия между `HEAD, GET, POST, PUT`?](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/networking/difference_between_head_get_post_put.md)
- Как загрузить что-то из интернета? В чем разница между `синхронными и асинхронными запросами`? 
- [Небольшое задание. Опишите как загрузить изображение из интернета и отобразить его в ImageView — все это должно происходить после нажатия кнопки.]()
- [Архитектура REST](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/networking/rest.md)


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






----------------------------
За список вопросов и часть ответов спасибо:
* [Torlopov-Andrey](https://github.com/Torlopov-Andrey)
