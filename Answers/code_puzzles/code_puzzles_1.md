## Что произойдет при исполнении следующего кода?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

```Objective-C
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];
```

Код скомпилируется. Но в будущем может упасть. Так как `release` в конце `Eventloop` будет послан уже удаленному объекту.

|№|Код|Описание|
|---|---|---|
|1| [Ball alloc]| Создаем объект `Ball` и в последствии он должен быть уничтожен.|
|2|[Ball alloc] init]| Инициализируем объект.|
|3|[[[Ball alloc] init] autorelease]| Добавляем объект в текущий `autorelease pool`,таким образом память будет освобождена когда `pool` будет очищаться.|
|4|[[[[Ball alloc] init] autorelease] autorelease]|Снова добавляем `Ball` в autorelease pool.  На 100% неправильно! Код скомпилируется, запуститься. Но в определенный момент приложение "упадет".|
