## Квадратные скобки для доступа к элементам массива или словаря можно использовать и со своими объектами.
(Новый синтаксис применим к любым объектам)

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)


Квадратные скобки для доступа к элементам массива или словаря можно использовать и со своими объектами. Для этого надо объявить следующие методы.

Для доступа по индексу:
```Objective-C
- (id)objectAtIndexedSubscript:(NSUInteger)index;
- (void)setObject:(id)obj atIndexedSubscript:(NSUInteger)index;
```

Для доступа по ключу:
```Objective-C
- (id)objectForKeyedSubscript:(id)key;
- (void)setObject:(id)obj forKeyedSubscript:(id)key;
```

Используем:
```Objective-C
id a = obj[1];
obj[@"key"] = a;
```

Рекомендации по использованию: иногда можно, но только если Ваш класс не является коллекцией. Если является, лучше наследоваться от имеющихся.

**Дополнительно**
* [Источник + доп материал.](https://habrahabr.ru/company/mailru/blog/210672/)
