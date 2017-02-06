## Как работают `push нотификации`?

[**Вернутся к списку вопросов**](https://github.com/CoBug92/Interview_iOS/blob/master/README.md)



**Иерархия компонентов**
* Основой иерархии UI-компонентов iOS приложения является объект UIWindow.
* UIWindow создается при запуске приложения. Далее, все UI-компоненты добавляются как дочерние на UIWindow.
* Обычно, приложение содержит только один объект типа UIWindow.


**UIWindow занимается следующим:*** Отображает ваш контент* Сообщает своим под-компонентам о событиях взаимодействия пользователя с UI 
* Сообщает контроллерам о поворотах устройства

**Обработка touch-событий**
Для обработки взаимодействия пользователя с UI и внешних событий в iOS используется механизм Responder Chain.
**Для touch-событий:*** UIWindow пытается передать touch в объект типа UIView, в котором он был вызван (hit-testing).* Если UIView не может обработать данный touch (например, объект в данный момент невидим, либо отключил возможность взаимодействия с собой), touch передается в superview данного компонента, и так далее вверх, пока он не будет обработан.

**Responder chain**Классы UIApplication, UIViewController и UIView наследуются от класса UIResponder.* UIResponder определяет порядок, в котором объекты обрабатывают события (touch-события, события от элементов UI (кнопки, слайдеры), изменение текста)* UIResponder объявляет методы, которые позволяют объектам определять, кто первым будет отвечать и обрабатывать сообщения:	* becomeFirstResponder — объект-получатель сообщения будет первым получать все события, посылаемые системой.	* resignFirstResponder — объект-получатель отказывается от обработки сообщений первым.

![alt text](https://developer.apple.com/library/content/documentation/General/Conceptual/Devpedia-CocoaApp/Art/iOS_and_OSX_responder_chain_2x.png "Responder chain")


**UIControl: Target-action**
Для обработки стандартных действий пользователя с UI (нажатие кнопки, изменение значения слайдера и тд) в UIKit / AppKit используется механизм target-action.* UI-компоненты, которые могут посылать сообщения, наследуются от UIControl — класс-наследник UIView, конкретизирующий обработку действий пользователя и выполнения связанных с ними действий.* Так же позволяют задать внешний вид компонента при определенном состоянии (выбран, нажат)

```swift
//допустим, мы создаем кнопку в методе viewDidLoad UIButton* button = [UIButton new];
[button addTarget:self action:@selector(buttonPressed:) forControlEvents:UIControlEventTouchDown];
....
- (void) buttonPressed:(id) sender {
}

```

### Статьи по теме

* [Лекция от Sibers](http://www.sibers.ru/wp-content/uploads/sibers-iOS-Lectures-5.pdf)
* [Habrahabr](https://habrahabr.ru/post/276799/)