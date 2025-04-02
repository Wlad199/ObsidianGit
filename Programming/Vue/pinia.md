#vue/pinia  |  [pinia](https://pinia-ru.netlify.app/introduction.html)
## Базовое использование
```js
// main.js

import { createPinia } from "pinia";
app.use(createPinia())
```
```js
// stores/counterStore.js

import { defineStore } from "pinia";

export let useCounterStore = defineStore('counter', {
// Состояние
	state() {
		return {
			count: 0
		}
	},
// Действия
	actions: {
		increment() {
			if (this.count < 10) {
				this.count++
			}
		}
	},
// Вычисляемые совойства
	getters: {
		remaining() {
			return 10 - this.count
		}
	}
})
```
```html
Component.vue

<template>
	<span>Counter:{{ counter.count }}</span>
	<button @click="counter.increment">Remains: {{ counter.remaining }}</button>
</template>

<script setup>
import { useCounterStore } from "@/stores/counterStore";
let counter = useCounterStore()
</script>
```

## Composition API + TS
```js
import { defineStore } from "pinia";

export const useTodoStore = defineStore('todoStore', () => {
	const todos = ref<ITodo[]>([])
	
// State
	const addNewTodo = (inputValue: string): void => {
		if (inputValue.length > 0) {
			todos.value.push({
				id: nanoid(),
				text: inputValue,
				completed: false
			})
		}
	}
	
// Actions
	const deleteTodo = (id: string): void => {
		todos.value = todos.value.filter(todo => todo.id !== id)
	}
	const changeStatus = (id: string): void => {
		let chossenTodo = todos.value.find(todo => todo.id === id)
		if (chossenTodo) {
			chossenTodo.completed = !chossenTodo.completed
		}
	}
	
// Return
	return {
		todos,
		addNewTodo,
		deleteTodo,
		changeStatus
	} as const
	// return {...} as const запретит напрямую мутировать стейт (аналог readonly)
})
```
## Дополнительно
### Деструктуризация:
```js
	import { useCounterStore } from '@/stores/counter' 
	import { storeToRefs } from 'pinia' 

	const store = useCounterStore() 

// Переменные
	const { name, doubleCount } = storeToRefs(store)
// Методы
	const { increment } = store
```
### Типизация Состояния
```ts
// для изначально пустых списков
	userList: [] as UserInfo[],
// для данных, которые еще не загружены
	user: null as UserInfo | null,
```
###  Наблюдать за всем состоянием экземпляра
```js
watch(
  pinia.state,
  (state) => {
    // сохранять все состояние в local storage при каждом его изменении
    localStorage.setItem('piniaState', JSON.stringify(state))
  },
  { deep: true }
)
```
