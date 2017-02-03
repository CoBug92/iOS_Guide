## Распечатать текущий autorelease pool

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

У ObjC имеются «скрытые» функции, доступ к которым можно получить с помощью `extern`:

```Objective-C
extern void _objc_autoreleasePoolPrint(void);
```

После вызова этой функции в консоль будет выведено содержимое текущего авторелиз-пула, примерно в таком виде:
```Objective-C
objc[26573]: ##############
objc[26573]: AUTORELEASE POOLS for thread 0x7fff72fb0310
objc[26573]: 9 releases pending.
objc[26573]: [0x100804000]  ................  PAGE  (hot) (cold)
objc[26573]: [0x100804038]  ################  POOL 0x100804038
objc[26573]: [0x100804040]       0x100204500  TestObject
objc[26573]: [0x100804048]       0x100102fc0  __NSDictionaryM
objc[26573]: [0x100804050]       0x1007000b0  __NSArrayI
objc[26573]: [0x100804058]       0x1006000a0  __NSCFString
objc[26573]: [0x100804060]       0x100600250  NSMethodSignature
objc[26573]: [0x100804068]       0x100600290  NSInvocation
objc[26573]: [0x100804070]       0x100600530  __NSCFString
objc[26573]: [0x100804078]       0x100600650  __NSArrayI
objc[26573]: ##############
```

Это бывает очень полезно для дебага. Можно поискать и другие полезные штуки [здесь](www.opensource.apple.com/source/objc4/objc4-551.1)
<br/>Рекомендации по использованию: в дебаге — пожалуйста.


**Дополнительно**
* [Источник + доп материал.](https://habrahabr.ru/company/mailru/blog/210672/)
