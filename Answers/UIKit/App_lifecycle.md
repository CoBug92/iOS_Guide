## Цикл жизни ios-приложения.

[**Вернутся к списку вопросов**](https://github.com/CoBug92/Interview_iOS/blob/master/README.md)

Сначала приложение не запущенно. Потом пользователь запускает приложение. Оно переходит в состояние Foreground, в котором приложение становится сначала Inactive —  на этом этапе выполняется код программы, но не обрабатываются события интерфейса пользователя (интерфейс не отображается, касания не обрабатываются и.т.п.). Затем переходит в этап Active, в котором выполняется код и обрабатываются все события UI.
Если пользователь запустит другое приложение, то текущее приложение перейдет в состояние Inactive и затем в состояние Background. В этом состоянии коды выполняется ограниченное время, и не обрабатываются события UI. Нужно понимать, что именно в этом состоянии можно заставить приложения получить, допустим, из интернета самые свежие обновления чего либо, и дать их приложению, что бы когда пользователь вернул приложение в Foreground он мог увидеть эту информацию.
После весьма короткого состояния Background  приложение переходит в состояние Suspended. В этом состоянии код не выполняется вовсе и система может убить приложение для освобождения памяти, если оно потребуется.

P.S. Ниже вы можете прочитать подробную информацию по жизненному циклу iOS-приложений на английском языке взятой с официальной документации Apple.

![Диаграмма на русском](http://proswift.ru/wp-content/uploads/2015/10/AplicationLifeCycle_proSwift_ru-600x648.jpg)

|State      | Description|
|-----------|------------|
|Not running|The app has not been launched or was running but was terminated by the system.|
|Inactive| The app is running in the foreground but is currently not receiving events. (It may be executing other code though.) An app usually stays in this state only briefly as it transitions to a different state.|
|Active|The app is running in the foreground and is receiving events. This is the normal mode for foreground apps.|
|Background|The app is in the background and executing code. Most apps enter this state briefly on their way to being suspended. However, an app that requests extra execution time may remain in this state for a period of time. In addition, an app being launched directly into the background enters this state instead of the inactive state. For information about how to execute code while in the background, see Background Execution.|
|Suspended| The app is in the background but is not executing code. The system moves apps to this state automatically and does not notify them before doing so. While suspended, an app remains in memory but does not execute any code. When a low-memory condition occurs, the system may purge suspended apps without notice to make more space for the foreground app.|


![Диаграмма на английском](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Art/high_level_flow_2x.png)


### Статьи по теме
[Описание в документации apple](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/TheAppLifeCycle/TheAppLifeCycle.html)

[Описание на русском](http://proswift.ru/ios-application-lifecycle-ili-zhiznennyj-cikl-ios-prilozheniya/)
