## Неявные property.

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

Объявление @property в хедере на самом деле объявляет лишь геттер и мутатор для некоторого поля. Если их объявить напрямую, ничего не изменится:
```Objective-C
- (int)value;
- (void)setValue:(int)newValue;

obj.value = 2;
int i = obj.value;
```

Так же неявные свойства — это любые функции, не принимающие аргументов, но возвращающие значение:
```Objective-C
NSArray *a = @[@1, @2, @3];
NSInteger c = a.count;
```

А ещё — функции, имя которых начинается на «set», ничего не возвращающие, но принимающие один аргумент:
```Objective-C
@interface TestObject : NSObject
- (void)setTitle:(NSString *)title;
@end;

//...

TestObject *obj = [TestObject new];
obj.title = @"simple object";
```

Рекомендации по использованию: объявление @property выглядит гораздо лучше, для этого и было введено. К свойствам лучше обращаться через ".", а вот обычные методы лучше вызывать через "[]". Иначе начинает сильно страдать читаемость кода.

**Дополнительно**
* [Источник + доп материал.](https://habrahabr.ru/company/mailru/blog/210672/)
