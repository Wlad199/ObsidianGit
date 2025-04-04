## LocalStorage 
#js/localstorage

localStorage  позволяет хранить пары ключ/значение в браузере.
key и value должны быть строками
Данные, которые в него записаны, сохраняются после обновления страницы и даже после перезапуска браузера
Этот объект один на все вкладки и окна в рамках источника (один и тот же домен/протокол/порт).

`setItem(key, value)` сохранить пару ключ/значение.
`getItem(key)` получить данные по ключу key.
`removeItem(key)` удалить данные с ключом key.
`clear()` удалить всё.
`key(index)` получить ключ на заданной позиции.
`length` количество элементов в хранилище.

Объекты веб-хранилища нельзя перебрать в цикле, они не итерируемы.
Но можно пройти по ним, как по обычным массивам (for, for in)
Здесь перебираются ключи, но вместе с этим выводятся несколько встроенных полей, которые нам не нужны
Поэтому нам нужно либо отфильтровать поля из прототипа проверкой `hasOwnProperty`
Либо просто получить «собственные» ключи с помощью Object.keys, а затем при необходимости вывести их при помощи цикла
`Object.keys` возвращает только ключи, принадлежащие объекту, игнорируя прототип
```js
let keys = Object.keys(localStorage);
for(let key of keys) {
	alert(`${key}: ${localStorage.getItem(key)}`);
}
```

Событие storage cрабатывает при вызове `setItem`, `removeItem`, `clear` со следующими свойствами:
`key` ключ, который обновился (null, если вызван .clear()).
`oldValue` старое значение (null, если ключ добавлен впервые).
`newValue` новое значение (null, если ключ был удалён).
`url` url документа, где произошло обновление.
`storageArea` объект localStorage, где произошло обновление.

событие срабатывает на всех остальных объектах window, где доступно хранилище, кроме того окна, которое его вызвало.
