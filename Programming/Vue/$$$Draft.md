### Вычисляемое свойство
```html
<p>Show weather in {{ city === '' ? 'your city' : cityName }}</p>
```
```js
export default {
	data() {
		return {
			city: ''
		}
	},
	computed: {
		cityName() {
			return '< ' + this.city + ' >'
		}
	}
}
```

### Импорт компонента 
#vue/import
```js
import AddTodo from './components/AddTodo.vue'
export default {
	components: { AddTodo }
}
```

### Фокус
#vue/focus
```html
<input v-focus type="text" placeholder="new todo" >

<script>
export default {
	directives: {
		focus: {
			mounted(el) {
				el.focus()
			}
		}
	}
}
</script>
```

### v-text
```html
<button v-text="button"></button>
// or
<button>{{button}}</button>
```