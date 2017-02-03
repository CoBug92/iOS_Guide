## Безымянные методы.

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)


Имя метода задавать не обязательно, если у него имеются аргументы. Нередко встречаются методы типа - (void)setSize:(CGFloat)x :(CGFloat)y, но это можно довести и до абсолюта:
```Objective-C
@interface TestObject : NSObject

+ (id):(int)value;
- (void):(int)a;
- (void):(int)a :(int)b;

@end

// ...

TestObject *obj = [TestObject :2];
[obj :4];
[obj :5 :7];
```

Забавно выгладят и селекторы для таких методов: @selector(:) и @selector(::).
Рекомендации по использованию: только в исследовательских целях.


**Дополнительно**
* [Источник + доп материал.](https://habrahabr.ru/company/mailru/blog/210672/)
