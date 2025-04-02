## Обработка инпута 
#vue/input

````html
  <div>
    <input @input="insertData($event.target.value)" type="text">
  </div>
  <div>
    <p>{{ userName }}</p>
  </div>
````

````js
	export default {
	  data() {
	    return {
	      userName: '',
	    }
	  },
	  methods: {
	    insertData(val) {
	      this.userName = val
	    }
	  }
	}
````
### Записать текст из инпута в переменную
```html
<input @input="this.city = $event.target.value">
// or
<input v-model="city">
```
