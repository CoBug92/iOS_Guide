## Разница между свойствами bounds и frame объекта UIView? Понимание системы координат?

[**Вернутся к списку вопросов**](https://github.com/CoBug92/Interview_iOS/blob/master/README.md)

Frame – это прямоугольник описываемый положением location(x, y) и размерами size (width, height) view относительно ее superview в которой она содержится. 
Bounds – это прямоугольник описываемый положением location(x, y) и размерами size (width, height) view относительно ее собственной системы координат (0, 0).


### Статьи по теме

* [UIView — UIView.frame и UIView.bounds](http://proswift.ru/poleznye-svojstva-cgrect-a-takzhe-svojstva-uiview-frame-i-bounds/)
* [Понимание системы координат](http://spec-zone.ru/RU/XCode/documentation/General/Conceptual/Devpedia-CocoaApp/CoordinateSystem.html)