## Доступ к публичным ivar-ам как в структурах.

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)


Несмотря на очевидность данной фичи, многие разработчики о ней почему-то не знают. Знание это может быть полезно для разрешения конфликта имён.
```Objective-C
@interface TestObject : NSObject
{
@public
	int field;
}

@implementation TestObject

- (void)updateWithField:(int)field
{
	self->field = field;
}

@end

// ...

TestObject *obj = [TestObject new];
obj->field = 200;
```

Рекомендации по использованию: в `ObjC` лучше для таких целей использовать `@property`.

**Дополнительно**
* [Источник + доп материал.](https://habrahabr.ru/company/mailru/blog/210672/)
