#vue/todo
### store.js
```js
import { reactive } from "vue";
import { nanoid } from 'nanoid'

export const store = reactive({
	todos: [],
	inputValue: '',
	addTodo() {
		this.todos.push({
			id: nanoid(),
			text: this.inputValue,
			completed: false
		})
		this.inputValue = ''
	},
	toggleStatus(id) {
		const currentTodo = this.todos.find(todo => todo.id === id)
		if (currentTodo) {
			currentTodo.completed = !currentTodo.completed
		}
	},
	deleteTodo(id) {
		this.todos = this.todos.filter(todo => todo.id !== id)
	}
})
```
### App.vue
```html
<template>
	<h1>Todo App</h1>
	<AddTodo />
	<TodoList />
</template>

<script>
import AddTodo from './components/AddTodo.vue'
import TodoList from './components/TodoList.vue'

export default {
	components: { AddTodo, TodoList }
}
</script>
```
### AddTodo.vue
```html
<template>
	<div>
		<label>
			<p>Add New Todo</p>
			<input 
				v-model="store.inputValue" 
				type="text" 
				placeholder="new todo" 
				v-focus>
		</label>
		<button @click="store.addTodo()">Add Todo</button>
	</div>
</template>

<script>
import { store } from '../store.js'
export default {
	data() {
		return {
			store,
		}
	},
	directives: {
		focus: {
			mounted(el) {
				el.focus()
			},
			updated(el) {
				el.focus()
			},
		}
	}
}
</script>
```
### TodoList.vue
```html
<template>
	<h2>Todo List:</h2>
	<ul>
		<TodoItem 
			v-for="todo in store.todos" 
			:key="todo.id" 
			:text="todo.text" 
			:completed="todo.completed" 
			:id="todo.id" />
	</ul>
</template>

<script>
import { store } from '../store.js';
import TodoItem from './TodoItem.vue'
export default {
	components: {
		TodoItem
	},
	data() {
		return {
			store
		}
	}
}
</script>
```

### TodoItem.vue
```html
<template>
	<li>
		<button 
			@click="store.toggleStatus(id)" 
			:class="[completed ? 'todo done' : 'todo']">
			{{ completed ? 'done ' : 'processing' }}
		</button>
		<span>{{ text }}</span>
		<button @click="store.deleteTodo(id)">delete</button>
	</li>
</template>

<script>
import { store } from '../store.js';
export default {
	props: {
		text: {
			type: String
		},
		completed: {
			type: Boolean
		},
		id: {
			type: String
		}
	},
	data() {
		return {
			store
		}
	}
}
</script>
```