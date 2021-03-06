## Что такое `состояние гонки`?

[**Вернутся к списку вопросов**](https://github.com/CoBug92/Interview_iOS/blob/master/README.md)

При работе многопоточного кода один поток может зависеть от результатов работы другого. И если мы неправильно запрограммируем код, будет получатся, что
разные потоки выполняются в разное время, и поток зависящий от результатов другого потока будет получать неверные значения.

На практике будет следующее: программа по непонятным причинам будет возвращать неверный результат. Но при попытке отладить - программа будет возвращать верное решение. Это происходит из-за того, что во время отладки, поток успеет выдать результат. Также ошибка может появится в случае с переходом на новое устройство. В старом был более слабый процессор и приложение работало как надо, а на новом устройстве приложение в одном из 1000 случаев не справляется.

Вместо того чтобы правильно расставить "барьеры" (в `GCD`) или зависимости операций (`NSOperationQueue`), разработчики начинают в потоке искусственно ставить торможение, чтобы другие потоки успели докачаться либо как-то иначе извращаются.


Мы можем воспроизвести простейший случай race condition, если будем изменять переменную value асинхронно на private очереди, а показывать value на текущем потоке:

‘’’Swift

print("--- Имитация race condition ---")
var value = "😇"
func changeValue(variant: Int) {
    sleep(1)
    value = value + "🐔"; print ("\(value) - \(variant)");
}
//: Запускаем `changeValue()` АСИНХРОННО и показываем `value` на текущем потоке
mySerialQueue.async {
    changeValue(variant: 1)
}
value
//: Теперь переустановим `value`, а затем выполним `changeValue()` __СИНХРОННО__, блокируя текущий поток до тех пор, пока задание `changeValue` не закончится, убирая таким образом 
race condition:
value = "🦊"
mySerialQueue.sync {
    changeValue(variant:2)
}
value
sleep(3)
‘’’

У нас есть обычная переменная value и обычная функция changeValue для ее изменения, причем умышленно мы сделали с помощью оператора sleep(1) так, что изменение переменной value требует значительного времени. Если мы будем запускать функцию changeValue АСИНХРОННО с помощью async, то прежде, чем дойдет дело до размещения измененного значения в переменной value, на текущем потоке переменная value может быть переустановлена в другое значение, это и есть race condition.

Давайте заменим метод async на sync:

‘’’Swift
//: Запускаем `changeValue()` СИНХРОННО и показываем `value` на текущем потоке
print("--- Убираем race condition с помощью sync---")
value = "😇"
mySerialQueue.sync {
    changeValue(variant: 1)
}
value
//: Теперь переустановим `value`, а затем выполним `changeValue()` __СИНХРОННО__, блокируя текущий поток до тех пор, пока задание `changeValue` не закончится, убирая таким образом 
race condition:
value = "🦊"
mySerialQueue.sync {
    changeValue(variant:2)
}
value
sleep(2)
‘’’

Мы видим, что хотя нужно быть очень внимательным с методом sync для очередей, потому что «текущий поток» вынужден ждать окончания выполнения задания на другой очереди, метод sync оказывается очень полезным для того, чтобы избежать race conditions.

### Статьи по теме
[Многопоточность](https://habrahabr.ru/post/320152/)