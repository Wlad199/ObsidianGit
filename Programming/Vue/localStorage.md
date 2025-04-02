### Использование внутри компонента
#vue/localStorage

```js
// localStorage
// При монтировании проверять наличие данных в localStorage
onMounted(() => {
	const savedTransactions = JSON.parse(localStorage.getItem('transactions'))
	if (savedTransactions) {
		transactions.value = savedTransactions
	}
})

// Ф-я записи данных в localStorage
const saveTransactionsToLacaleStorage = () => {
	localStorage.setItem('transactions', JSON.stringify(transactions.value))
}

// Вызывать ф-ю записи во всех ф-ях, которые меняют данные
const addNewTransaction = (transaction) => {
	************
	saveTransactionsToLacaleStorage()
}
const deleteTransaction = (id) => {
	*************
	saveTransactionsToLacaleStorage()
}
```

### Сохранение в хранилище (в отдельном файле)
[vue: useStorage](https://www.youtube.com/watch?v=HJAImAlZzxk&list=PL3VM-unCzF8jX-GoazLPcbi7M0wJux8F-&index=20)
- Ф-я useStorage записывает значения по ключу key
- Через localStorage.getItem получить значение и сделать его реактивным
- Повесить прослушку watch на реактивное значение
- Выполнять перезапись при его изменении
- Удалять ключ если нет значения
```html
component.vue

<template>
	<input type="text" placeholder="enter food" v-model="food">
	<input type="text" placeholder="enter age" v-model="age">
</template>

<script setup>
import { useStorage } from '../composables/useStorage'
let food = useStorage('food')
let age = useStorage('age')
</script>
```

```js
// composables/useStorage.js

import { ref, watch } from 'vue'

export function useStorage(key) {
	let storedValue = localStorage.getItem(key)
	let val = ref(storedValue)
	
	watch(val, write)

	function write() {
		if (val.value === '') {
			localStorage.removeItem(key)
		} else {
			localStorage.setItem(key, val.value)
		}
	}
	return val
}
```

### Store + watch
```ts
	const todos = ref<ITodo[]>([])

	let todosInLocalStorage = JSON.parse(localStorage.getItem('todos') || '')
	if (todosInLocalStorage) {
		todos.value = todosInLocalStorage
	}

	watch(() => todos, (state) => {
		localStorage.setItem('todos', JSON.stringify(state.value))
	}, { deep: true })

```
### Фикс ошибки для TS
- возвращаемое значение не должно быть null, поэтому `as string` или: 
```ts
	const todosInLocalStorage = JSON.parse(localStorage.getItem('todos') || '')
```