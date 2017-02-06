## Как работает UITableView?

[**Вернутся к списку вопросов**](https://github.com/CoBug92/Interview_iOS/blob/master/README.md)

Таблица имеет три основных составляющие: саму таблицу, разделы таблицы (или группировки) и ячейки таблицы (отдельные строки в таблице). Данные в таблицы помещаются в очередь из источника данных таблицы. Источник данных - это объект, предоставляющий таблице информацию о том, какие данные отображать, например, имена файлов, сообщения электронной почты и т. д. Для облегчения понимания работы с таблицей возьмем обычный массив, в который будут включены только строки.

При работе с таблицами есть несколько обязательных функций:


К примеру у нас есть массив restaurant: [String] = [«Barrafina», «Cafe Deadend», «Confessional»]

1. В первую очередь, следует указать сколько секций будет в нашей таблице. Делается это с помощью метода numberOfSectionsInTableView. Так как я изначально хочу чтобы была только 1 секция содержащая название ресторанов, то я так и указываю.

```swift

override func numberOfSections(in tableView: UITableView) -> Int {

        return 1    //Count of sections in TableView

    }
```

2. Чтобы "сказать" нашей таблице сколько в ней будет строк (а их будет столько же, сколько и элементов в источнике данных) используйте метод numberOfRowsInSection

Встроенной функцией подсчитываю кол-во элементов в массиве restaurant.

```swift

override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {

            return restaurants.count

    }
```

3. Теперь нам нужно заполнить ячейки нашей таблицы. Для заполнения воспользуйтесь методом cellForRowAtIndexPath. Он предоставляет нам “indexPath” (тип “NSIndexPath“). С помощью данного значения мы сможем выяснить текущий номер строки, чтобы заполнить ее элементом источника с таким же индексом. В самом методе cellForRowAtIndexPath уже имеется код, отвечающий за поиск и создание ячейки.

Присваиваем лейблу в ячейке значение элемента массива с индексом indexPath

```swift

override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {

	let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath)

        //Configurate the cell:

	cell.nameLabel.text = restaurant.name

	return cell

    }
```
 