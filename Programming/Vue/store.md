#vue/store
- store.js
```js
import { reactive } from "vue";
import { nanoid } from 'nanoid'

export const store = reactive({
	todos: [],
	addTodo() {
	...
	}
})
```
- Component.vue
```html
<div>
	<button @click="store.addTodo()">Add Todo</button>
</div>

<script>
import { store } from '../store.js'

	export default {
		data() {
			return {
				store
			}
		}
	}
</script>
```