## `Селектор (selector).`

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

### Что такое `селектор (selector)`?

Селектор - это имя метода закодированное специальным образом, используемым objective-c для быстрого поиска. Указание компилятору на селектор происходит при помощи директивы @selector(метод)

```objective-c
First* f = [[First alloc] init];
if([f respondsToSelector:@selector(setName:)]){
  NSLog (@"Метод поддерживается");
}
```
В этом примере создается экземпляр класса `First *f` (наследник `NSObject`), после с помощью метода respondsToSelector проверяем может ли класс ответить на метод `setName`.


### Как его вызвать?
```Objective-C
[self performSelector:@selector(method)];
```

### Как отложить вызов селектора?
```Objective-C
[self performSelector:@selector(method) withObject:obj afterDelay:delay];
```

### Что делать если селектор имеет много параметров?

```Objective-C
@selector(method:::) - двоиточий столько сколько параметров.
```

### (NSInvocation)

Вызывает метод у объекта, можно менять параметры и цель.
Как запустить селектор во фоновом потоке?
```Objective-c
[self performSelectorInBackground:selector withObject:obj];
```
