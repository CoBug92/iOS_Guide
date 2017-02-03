## Что такое `deadlock`?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

`Deadlock` - это тупик. Один поток ждет освобождения второго, а второй ждет освобождения первого. Таким образом происходит зависание приложения.
Пример: в качестве делегата передаем себя как сильную ссылку. А в контроллере делегате пытаемся удалить делегат. В случае с потоками происходит зависание.

Обратная ситуация - [`livelock`](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/answers/multithreading/livelock.md)


```objective-c
dispatch_queue_t queue = dispatch_queue_create("my.label", DISPATCH_QUEUE_SERIAL);
dispatch_async(queue, ^{
    dispatch_sync(queue, ^{
        // outer block is waiting for this inner block to complete,
        // inner block won't start before outer block finishes
        // => deadlock
    });

    // this will never be reached
});

dispatch_queue_t q = dispatch_queue_create("deadlock queue", DISPATCH_QUEUE_SERIAL);
NSLog(@"1");
dispatch_async(q, ^{
    NSLog(@"2");
    dispatch_sync(q, ^{
        NSLog(@"3");
    });
    NSLog(@"4");
});
NSLog(@"5");

dispatch_sync(dispatch_get_current_queue(), ^{});
```

Шаг|Процесс 1|Процесс 2|
-|
0|Хочет захватить A и B, начинает с A| Хочет захватить A и B, начинает с B
1|Захватывает ресурс A|Захватывает ресурс B
2|Ожидает освобождения ресурса B|Ожидает освобождения ресурса A
3|Взаимная блокировка|Взаимная блокировка
