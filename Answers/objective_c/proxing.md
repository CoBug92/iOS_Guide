## Проксирование: forwardingTargetForSelector: и forwardInvocation:

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)


Для ООП свойственно введение дополнительных уровней абстракции при некоторых проблемах. К примеру, иногда нужно из объекта сделать прокси для другого объекта. В этом нам всегда помогут следующие методы.

Если в нашем объекте не найдена имплементация для некоторого селектора, то ему будет послано следующее сообщение:

```Objective-C
- (id)forwardingTargetForSelector:(SEL)aSelector
{
	if ([_dict respondsToSelector:aSelector])
	{
		return _dict;
	}
	return [super forwardingTargetForSelector:aSelector];
}
```

Если объект, который мы проксируем, отвечает на селектор, то пусть он и реагирует на него. Иначе всё таки придётся кинуть эксепшн.

Если мы хотим не просто передать селектор другому объекту, но при этом и изменить сам селектор, мы можем воспользоваться следующей парой функций.

Сначала на запрос сигнатуры неизвестного нам метода мы должны вернуть сигнатуру существующего метода проксируемого объекта:
```Objective-C
- (NSMethodSignature *)methodSignatureForSelector:(SEL)aSelector
{
	NSMethodSignature *sig = [super methodSignatureForSelector:aSelector];
	if ([NSStringFromSelector(aSelector) isEqualToString:@"allDamnKeys"])
	{
		sig = [_dict methodSignatureForSelector:@selector(allKeys)];
	}
	return sig;
}
```

Затем перенаправляем вызов и меняем имя селектора:
```Objective-C
- (void)forwardInvocation:(NSInvocation *)anInvocation
{
	if ([NSStringFromSelector(anInvocation.selector) isEqualToString:@"allDamnKeys"])
	{
		anInvocation.selector = @selector(allKeys);
		[anInvocation invokeWithTarget:_dict];
	}
}
```

Рекомендации по использованию: очень удобный механизм для реализации прокси-объектов. Возможно, кто-то найдёт и другие варианты использования. Главное — не переусердствовать: код должен быть читаем и легко понимаем.


**Дополнительно**
* [Источник + доп материал.](https://habrahabr.ru/company/mailru/blog/210672/)
