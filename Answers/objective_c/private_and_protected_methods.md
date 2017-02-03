## Есть ли `приватные и защищенные` методы в Objective-C?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

Нет, таких методов нет. Но можно реализовать их иммитацию.

```Objective-C
/////// SuperClass.h
@interface SuperClass  @end

/////// SuperClass.m
@implementation SuperClass
- (void) protectedMethod
{}
@end

/////// SubClass.h
@interface SubClass : SuperClass
@end

/////// SubClass.m
@interface SubClass (Protected)
- (void) protectedMethod ;
@end

@implementation SubClass
- (void) callerOfProtectedMethod
{
  [self protectedMethod] ; // this will not generate warning
}
@end
```
