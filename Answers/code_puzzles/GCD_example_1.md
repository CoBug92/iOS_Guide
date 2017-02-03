## Что выведется в консоль?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)


```Objective-C
 dispatch_async(dispatch_get_main_queue(), ^
    {
        NSLog(@"A %d", [object retainCount]);
        dispatch_async(dispatch_get_main_queue(), ^
        {
            NSLog(@"B %d", [object retainCount]);
        });
        NSLog(@"C %d", [object retainCount]);
    });
    NSLog(@"D %d", [object retainCount]);
```

В коде надо добавить хотя бы это:
```Objective-C
 NSObject *object = [NSObject new]
```
Иначе проект не скомпилируется. После добавления в лог выведется следующее:
```
>> D 2
>> A 2
>> C 3
>> B 2
```
