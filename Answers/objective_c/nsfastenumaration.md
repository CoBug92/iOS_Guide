## Что не так с этим кодом? Зачем нужны `инициализаторы`?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

Что ж, в заключение ещё одна интересная фича `ObjC`: циклы `for..in`. Их поддерживают все дефолтные коллекции, но можем поддержать и мы. Для этого надо поддержать протокол `NSFastEnumeration`, а точнее — определить метод `countByEnumeratingWithState:objects:count:`, но не всё так просто! Вот сигнатура этого метода:

```Objective-C
- (NSUInteger)countByEnumeratingWithState:(NSFastEnumerationState *)state objects:(id __unsafe_unretained [])buffer count:(NSUInteger)len
```

Этот метод будет вызван каждый раз, когда runtime захочет получить от нас новую порцию объектов. Их мы должны записать либо в предоставленный буфер (размер его len), либо выделить свой. Указатель на этот буфер надо поместить в поле `state->itemsPtr`, а количество объектов в нём вернуть из функции. Так же не забываем, что (в документации этого нет) поле `state->mutationsPtr` не должно быть пустым. Если этого не сделать, то мы получим неожиданный `SEGFAULT`. А вот в поле `state->state` можно записать что угодно, но лучше всего — записать количество уже отданных элементов. Если отдавать больше нечего, нужно вернуть ноль.

Вот мой пример реализации этой функции:
```Objective-C
- (NSUInteger)countByEnumeratingWithState:(NSFastEnumerationState *)state objects:(id __unsafe_unretained [])buffer count:(NSUInteger)len
{
	if (state->state >= _value)
	{
		return 0;
	}
	NSUInteger itemsToGive = MIN(len, _value - state->state);
	for (NSUInteger i = 0; i < itemsToGive; ++i)
	{
		buffer[i] = @(_values[i + state->state]);
	}
	state->itemsPtr = buffer;
	state->mutationsPtr = &state->extra[0];
	state->state += itemsToGive;
	return itemsToGive;
}
```

Теперь можно использовать:
```Objective-C
for (NSNumber *n in obj)
{
	NSLog(@"n = %@", n);
}
```

Рекомендации по использованию: может быть полезно для упрощения работы с кастомными структурами данных, к примеру, с деревьями и связанными списками.

**Дополнительно**
* [Источник + доп материал.](https://habrahabr.ru/company/mailru/blog/210672/)
