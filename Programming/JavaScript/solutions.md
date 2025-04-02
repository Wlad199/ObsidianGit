
### Добавление свойств в массив объектов
```js
const response = await axios.get('https://reqres.in/api/users')
const data = await response.data.data
modifyData = data.map(user => ({ ...user, isInvited: false }))
```

### Вывод даты
```js
	{{ new Date().toLocaleDateString('en-us', {
		weekday: 'long',
		year: 'numeric',
		month: 'long',
		day: 'numeric'
	}) }}
```

### Поиск с задержкой
Чтобы запрос не срабатывал при каждом нажатии установить таймер и очищать его
```js
	const query = ref<string>('')
	const timeOut = ref(null)
	
	const handleSearch = () => {
		clearTimeout(timeOut.value)
		timeOut.value = setTimeout(async () => {
			const response = await fetch(`
				http://api.weatherapi.com/v1/search.json
				?key=e06a680c7a934767860155344252402&q=${query.value}
			`)
			const data = await response.json()
		}, 500)
	}
```

### Вывод кастомной даты
```js
	new Date().toLocaleDateString('en-us', {
		weekday: 'long',
		year: 'numeric',
		month: 'long',
		day: 'numeric'
	})
```

### Проблема с импортом Json в ts
```json
// tsconfig.app.json

	"compilerOptions": {
		"resolveJsonModule": true,
		"esModuleInterop": true,
		
		"module": "commonjs",
		"moduleResolution": "node",
		"outDir": "dist",
		"rootDir": "src",
		"target": "es6",
	}
```
### Перезагрузить страницу
```js
window.location.reload()
```