## Суть `рантайма (Runtime), отправление сообщения`.

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

<br/><br/>
[Вот тут подробно расписиано](https://habrahabr.ru/post/177421/)

Метды рантайма описаны в заголовочных файлах: objc.h, runtime.h и message.h

`Runtime`, библиотека времени выполнения, предоставляет тот набор функций, которые "вдыхают" в язык жизнь, реализуя его динамические возможности и обеспечивая функционирование ООП.

Класс в Objective-C — это полноценный объект и у него тоже присутствует isa-указатель на «класс класса», так называемый метакласс в терминах Objective-C. Аналогично, С-структуры определены и для других сущностей языка:

#### Функции Runtime-библиотеки

Помимо определения основных структур языка, библиотека включает в себя набор функций, работающих с этими структурами. Их можно условно разделить на несколько групп (назначение функций, как правило, очевидно из их названия):
* Манипулирование классами: class_addMethod, class_addIvar, class_replaceMethod
* Создание новых классов: class_allocateClassPair, class_registerClassPair
* Интроспекция: class_getName, class_getSuperclass, class_getInstanceVariable, class_getProperty, class_copyMethodList, class_copyIvarList, class_copyPropertyList
* Манипулирование объектами: objc_msgSend, objc_getClass, object_copy
* Работа с ассоциативными ссылками
