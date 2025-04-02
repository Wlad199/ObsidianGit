#css
#### backdrop-filter
	backdrop-filter: blur(5px)
#### [Фильтр цвета ](https://thecode.media/hue-rotate)
#### Запретить взаимодействие курсором 
`pointer-events: none`
`user-select: none`
#### Запретить выделение текста 
`user-select: none`
#### Зачеркнутый текст 
`text-decoration: line-through`
`text-decoration-color: red`  Выбрать цвет
#### Убирать маркеры списка 
`list-style-type: none`
#### svh, lvh, dvh 
Lvh (large viewport height) задает размеры по самому большому размеру viewport, когда панель навигации скрыта.

Svh (Small viewport height). Данная единица измерения задает самый маленький размер viewport, когда панель навигации отображается.

Dvh (Dynamic viewport height) динамически меняет значение высоты относительно того, открыта панель с навигацией или нет.

####  Ленивая загрузка 
`loading = "lazy"`

#### [E-mail & Te](https://htmlacademy.ru/blog/html/mailto)
`<a href="tel:+375291136969">+375 (29) 113-69-69</a>`
`<a href="mailto:mail@htmlacademy.ru">Напишите нам</a>`

#### [Социалки](https://itchief.ru/javascript/social-buttons)

#### max, min, clamp 
```css
.element {
  width: min(50%, 500px);
  Выберет наименьшее (наибольшее) значение
}
```

```css
.element {
  width: clamp(200px, 50%, 1000px);
  200px - минимальное значение, 1000px - максимальное, 50% - вычисляемое
  Примет вычисляемое значение, если оно в установленных пределах
}
```

#### Обрезать невлезающий текст
```css
.block{
  overflow: hidden;
  text-overflow: ellipsis;
  white-space:nowrap;
}

// or

.block{
  display: -webkit-box;
  overflow: hidden;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3; 3 строчки, далее ...
}
```

#### Соотношение сторон aspect-ratio 
```css
.container {
  width: 200px;
  aspect-ratio: 1 / 1;
}
```
  `auto` — соотношение сторон считается автоматически.
 ` <width> / <height>` — соотношение сторон всегда считается относительно ширины и высоты блока.
  `auto <width> / <height>` — совмещённая запись.
  Чтобы избежать искажений картинки, можно использовать свойство object-fit.
  Свойство нельзя применить к строчным элементам.


  

#### Подсказка при наведении 

```css
span:hover::after{
  content: attr(data-title);
}
```



  


  

#### В степень 
`<sup>Текст</sup>`

#### Градусы
`&deg`
  

#### Уменьшает размер шрифта 
Тег `<small>` уменьшает размер шрифта на единицу по сравнению с обычным текстом.

#### Подсказки
```html
<span data-title="Вывести подсказку"><img src="@img/s02.jpg" alt=""></span>
```

#### CSS Селекторы 

 Смежные селекторы (A + B)
 `.button + .button` Для всех, идущих после

 Братские селекторы (A ~ B)
 `.button ~ .button` Выбирает все братские элементы B, которые идут в коде после элемента A