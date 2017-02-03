## Что такое autorelease pool?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

Это специальный механизм, который позволяет посылать отложенное сообщение об освобождении объекта.
Чтобы использовать эту возможность надо объект зарегистрировать в этом пуле.

```Objective-C
@autoreleasepool {
    // Code benefitting from a local autorelease pool.
}
```
