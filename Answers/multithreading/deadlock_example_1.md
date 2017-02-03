## Выведется ли в дебагер «Hello world»? Почему?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

```Objective-C
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    dispatch_sync(dispatch_get_main_queue(), ^{
        NSLog(@"Hello world");
    });

   /* Another implementation */
   return YES;
}
```
Здесь имеет место быть классический deadlock. Чтобы вывести в лог, программа должна быть загружена. И выполнение блока
ждет когда вернется признак YES. В тоже время, признак YES не возвращается, так как ждет выполнение блока.
