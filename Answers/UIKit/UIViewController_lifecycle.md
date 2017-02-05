## Цикл жизни UIViewController.

[**Вернутся к списку вопросов**](https://github.com/CoBug92/Interview_iOS/blob/master/README.md)



Жизненный цикл контроллера начинает с создания. В 99% случаях создание происходит в storyboard, и «за сценой» происходит инициализация, а потом:
    1. Подготовка  к переходу в контроллер:  Другой контроллер приготавливается к переходу в наш. При этой подготовке outlet свойства еще не установлены. К ним обращаться нельзя!

```swift
 override func prepareForSegue(segue: UIStoryboardSegue, sender: AnyObject?)

```

    2. Установка outlet свойств

```swift
 @IBOutlet weak var pannableView: UIView {
 }

```

    3. Появление на экране и уход с экрана Это самое отличное место чтобы выполнить большинство установок для контроллера. Посудите сами — в подготовке все нужные данные переданы, свойства установлены — самое время что-то настроить.

```swift
 override func viewDidLoad() {
 super.viewDidLoad() // всегда вызываем метод жизненного цикла у суперкласса
 // настраиваем наш MVC
 }

``` Далее появления на экране: прямо перед появлением  view на экране мы получаем уведомление вызовом 

```swift
 override func viewWillAppear(animated: Bool) {
 super.viewWillAppear(animated)
  }

``` Далее, сразу после появления view на экране вызывается метод

```swift 
override func viewDidAppear(animated: Bool) { 
super.viewDidAppear(animated) 
}

``` Если view  ушло с экрана вызываются методы

```swift 
override func viewWillDisappear(animated: Bool) { 
super.viewWillDisappear(animated) 
} 
 override func viewDidDisappear(animated: Bool) { 
super.viewDidDisappear(animated) 
}

```

    4. Изменение геометрии (поворот, изменение границ) Система знает когда поменялись границы нашего view. И она вызывает методы

```swift 
super.viewWillLayoutSubviews() 
} 
//  Autolayout происходит тут - между двумя этими методами  
 override func viewDidLayoutSubviews() { 
super.viewDidLayoutSubviews() 
 }

``` 
Нужно понимать, что это не функция ВьюВКонтроллереИзменилаГраницы(). Расположение всех элементов пользовательского интерфейса задаются параметрами Autolayout , и эти два метода вызываются чтобы убедится, что расстановка выполнена правильно (до начала расстановки и сразу после нее) Обработка поворота экрана обрабатывается автоматически, и задается в настройках приложения. Однако если нужно самостоятельно обработать  анимацию при повороте, то можно использовать следующий метод, который также является частью жизненного цикла ViewController:

```swift 
func viewWillTransitionToSize(size: CGSize, withTransitionCoordinator coordinator: 

UIViewControllerTransitionCoordinator)

```

    5. Ситуация с недостатком памяти устройства Ну и в очень редких случаях система может послать сообщение о нехватке памяти

```swift 
override func didReceiveMemoryWarning()

``` 
Тут можно попробовать обнулить объекты, которые не используются.

