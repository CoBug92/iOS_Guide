## Какой метод вызовется: класса A или класса B? Как надо изменить код, чтобы вызвался метод класса A?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)


```objective-c
@interface A : NSObject
- (void)someMethod;
@end

@implementation A
- (void)someMethod
{
    NSLog(@"This is class A");
}
@end

@interface B : A
@end

@implementation B
- (void)someMethod
{
    NSLog(@"This is class B");
}
@end

@interface C : NSObject
@end

@implementation C
- (void)method
{
    A *a = [B new];
    [a someMethod];
}
```

Вызовется метод `класса B`.<br/>
Чтобы вызвался метод `класса А` надо изменить код одним из двух способов:

I способ:<br/>
Создаем объект класса А.

```objective-c
@implementation C
- (void)method
{
    A *a = [B new];
    [a someMethod];
}
```

II способ:<br/>
В имплементации класс B вызываем метод его супер-класса

```objective-c
@implementation B
- (void)someMethod
{
    [super someMethod];
}
@end
```
