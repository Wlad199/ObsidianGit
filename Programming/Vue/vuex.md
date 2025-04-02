#vue/vuex
[Vuex.com](https://vuex.vuejs.org/)
[Composition Examples](https://github.com/vuejs/vuex/tree/main/examples/composition)
## Основы

#### Установка
```sh
npm install vuex@next --save
```

## Теория
Единственный способ изменить состояние в хранилище Vuex — это выполнить мутацию.
Нельзя напрямую вызвать обработчик мутации. Думайте об этом скорее как о регистрации события: «При возникновении мутации с типом `increment` вызовите этот обработчик». Чтобы вызвать обработчик мутации, вам нужно вызвать `store.commit` с указанием его типа: `store.commit('increment')`
Функции обработчиков мутаций должны быть синхронными.
Чтобы обрабатывать асинхронные операции нужны экшэны.

Экшены аналогичны мутациям, с той разницей, что:
- Вместо того, чтобы изменять состояние, действия совершают мутации.
- Действия могут содержать произвольные асинхронные операции.

#### Composition Api
В Composition Api чтобы получить доступ к состоянию и геттерам, нужно  создать `computed` ссылки для сохранения реактивности. Это эквивалентно созданию вычисляемых свойств с помощью Option API.
```js
const count = computed(() => (store.state.count))
```

При доступе к мутациям и экшенам можно указать метод `commit` и `dispatch`
```js
// Мутации
	const increment = () => {
		store.commit('increment', 10)
	}
	
// Гетттеры
	const double = computed(() => store.getters.double)
```


## Options API
#### С мутацией в сторе
```js
// main.js

import { createApp } from 'vue'
import App from './App.vue'
import { store } from "./stores/store";

const app = createApp(App)
app.use(store)
app.mount('#app')
```
```js
// store.js

import { createStore } from "vuex";

export const store = createStore({
	state() {
		return {
			count: 1
		}
	},
	mutations: {
		increment(state) {
			state.count++
		}
	}
})
```
```html
App.vue

<template>
	<div>count: {{ store.state.count }}</div>
	<button @click="store.commit('increment')">increment</button>
</template>

<script setup>
import { store } from "./stores/store";
</script>
```
#### С мутацией в компоненте
```js
// store.js

import { createStore } from "vuex";

export const store = createStore({
	state() {
		return {
			count: 10
		}
	},
	mutations: {
		increment(state) {
			state.count++
		}
	}
})
```
```html
app.vue

<template>
	<div>count: {{ this.$store.state.count }}</div>
	<button @click="increment">increment</button>
</template>

<script >
export default {
	data() {
		return {
		}
	},
	methods: {
		increment() {
			this.$store.commit('increment')
		}
	}
}
</script>
```

## Composition API
#### С мутацией в сторе
```js
// main.js

import { createApp } from 'vue'
import App from './App.vue'
import store from "./stores/store";

const app = createApp(App)
app.use(store)
app.mount('#app')
```
```js
// store.js

import { createStore } from "vuex";

const state = {
	count: 1
}

const mutations = {
	increment(state) {
		state.count++
	},
	decrement(state) {
		state.count--
	}
}

export default createStore({
	state,
	mutations
})
```
```html
App.vue

<template>
	<div>count: {{ store.state.count }}</div>
	<button @click="store.commit('increment')">increment</button>
	<button @click="store.commit('decrement')">decrement</button>
</template>

<script setup>
import { useStore } from 'vuex';
const store = useStore()
</script>
```
#### С дополнительной нагрузкой
```js
// store.js

import { createStore } from "vuex";

// Состояние
const state = {
	count: 1
}

// Мутации
const mutations = {
	increment(state, payload) {
		state.count += payload
	},
	decrement(state, payload) {
		state.count -= payload.value
	}
}

// Геттеры
const getters = {
	double(state) {
		state.count *= 2
	}
}

// Экшены
const actions = {

	asyncIncrement(context, payload) {
		setTimeout(() => {
			context.commit('increment', payload)
		}, 1000);
	},
	
	asyncDecrement({ commit }, payload) {
		setTimeout(() => {
			commit('decrement', payload)
		}, 1000);
	},
}

export default createStore({
	state,
	mutations,
	getters,
	actions
})
```
```html
App.vue

<template>
	<div>count: {{ count }}</div>
	<button @click="increment">increment</button>
	<button @click="decrement(500)">decrement</button>
	<button @click="double">double</button>
	<button @click="asyncIncrement">Async increment</button>
	<button @click="asyncDecrement">Async decrement</button>
</template>

<script setup>
import { computed } from 'vue';
import { useStore } from 'vuex';

// Получить store
const store = useStore()

// count получить через computed
const count = computed(() => (store.state.count))

// ф-я вызывает мутацию с payload
const increment = () => {
	store.commit('increment', 10)
}
// payload может быть в виде объекта
const decrement = (sum) => {
	store.commit({
		type: 'decrement',
		value: sum,
	})
}

// Получить свойство из геттеров с помощью computed
const double = computed(() => store.getters.double)

// Экшены запускаются через dispatch
const asyncIncrement = () => {
	store.dispatch('asyncIncrement', 50)
}
const asyncDecrement = () => {
	store.dispatch({
		type: 'asyncDecrement',
		value: 1000
	})
}
</script>
```