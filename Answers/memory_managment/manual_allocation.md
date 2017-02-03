## Ручное выделение памяти под объект без alloc.

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)


Объекты можно создавать с помощью старой доброй сишной функции calloc, задав потом isa вручную. В принципе, это лишь замена alloc, а init можно отправить и потом.

```Objective-C
// Выделяем память, заполненную нулями
void *newObject = calloc(1, class_getInstanceSize([TestObject class]));
// Задаём isa прямой записью в память
Class *c = (Class *)newObject;
c[0] = [TestObject class];
// Здесь __bridge_transfer-каст нужен для передачи объекта в ARC - иначе утечёт
obj = (__bridge_transfer TestObject *)newObject;
// Посылаем init - объект готов!
obj = [obj init];
```

Рекомендации по использованию: рекомендуется с превеликой осторожностью. Один из вариантов использования — выделение памяти разом под большой массив объектов (о чём рассказывал некогда AlexChernyy на CocoaHeads).

UPD: Благодаря пользователю Trahman было установлено, что данный подход не работает на iOS x64. С его же помощью было найдено портабельное решение:

```Objective-C
object_setClass((__bridge id)newObject, [TestObject class]);
```

**Дополнительно**
* [Источник + доп материал.](https://habrahabr.ru/company/mailru/blog/210672/)
