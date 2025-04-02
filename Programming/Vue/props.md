###  Базовый случай
#vue/props

```html
TodoApp.vue

<template>
	<ul>
		<TodoItem 
			v-for="todo in store.todos" 
			:key="todo.id" 
			:text="todo.text" 
			:completed="todo.completed" 
			:id="todo.id" 
		/>
	</ul>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
	components: {
		TodoItem
	}
}
</script>
```

```html
TodoItem.vue

<template>
	<li>
		<button 
			:class="[completed ? 'todo done' : 'todo']">
			{{ completed ? 'done ' : 'processing' }}
		</button>
		<span>{{ text }}</span>
	</li>
</template>

<script>
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
	}
}
</script>
```

---
### Стилизация кнопок чарез пропсы 
 #vue/slot

![[button01.jpg]]

![[buton02.jpg]]
```html
App.vue

<template>
	<my-button typeButton="primary">first button</my-button>
	<my-button typeButton="secondary">second button</my-button>
	<my-button typeButton="muted">third button</my-button>
	<my-button :processing="true">forth button</my-button>
</template>

<script>
import MyButton from "./components/MyButton.vue";
export default {
	components: {
		'my-button': MyButton
	}
}
</script>

<style scoped>
.blue {
	background-color: #007acc;
}
.purpure {
	background-color: #c822af;
}
.gray {
	background-color: #aab0b6;
}
button:disabled {
	opacity: 0.3;
}
</style>
```

```html
MyButton

<template>
	<button 
		:class="{
			'button': true,
			'blue': typeButton === 'primary',
			'purpure': typeButton === 'secondary',
			'gray': typeButton === 'muted',
			'is-loading': processing
		}" 
		:disabled="processing">
		<slot />
	</button>
</template>

<script>
export default {
	props: {
		typeButton: {
			type: String,
			default: 'primary'
		},
		processing: {
			type: Boolean,
			default: false
		}
	},
}
</script>
```

---

### Добавление новой задачи из дочернего компонента в родительский массив задач
#### Обычный метод передачи 
- Передать весь родительский массив чарез пропсы в дочерний
- В дочернем добавить новую задачу
```html
App.vue

<AssignmentCrete :assignments="assignments" />
```

```html
AssignmentCreate.vue

<form @submit.prevent="add" action="#">
	<div>
		<input v-model="newAssignment" type="text" placeholder="add assignment...">
		<button>Add</button>
	</div>
</form>

<script>
export default {
	data() {
		return {
			newAssignment: ''
		}
	},
	props: {
		assignments: Array
	},
	methods: {
		add() {
			this.assignments.push({
				name: this.newAssignment,
				completed: false,
				id: this.assignments.length + 1
			})
			this.newAssignment = ''
		}
	}
}
</script>
```

#### Изменение родительского массива из дочернего компонента чарез ф-ю $emit
#vue/emit
- Ф-я добавления находится в родителе. Принимает в качестве параметра имя
- Дочернему компоненту добавлен обработчик события @add="add"
- В дочернем компоненте есть метод add, который через $emit вызывает родительский метод add и передает в качестве параметра состояние инпута
```html
app.vue

<AssignmentCrete @add="add" />

<script>
export default {
	methods: {
		add(name) {
			this.assignments.push({
				name: name,
				completed: false,
				id: this.assignments.length + 1
			})
		}
	}
}
</script>
```
```html
AssignmentCreate.vue

<form @submit.prevent="add" action="#">
	<div>
		<input v-model="newAssignment" type="text" placeholder="add assignment...">
		<button>Add</button>
	</div>
</form>

<script>
	export default {
		data() {
			return {
				newAssignment: ''
			}
		},
		methods: {
			add() {
				this.$emit('add', this.newAssignment)
				this.newAssignment = ''
			}
		}
	}
</script>
```

### Пробрасывание входных параметров, через provide-inject
#vue/provide #vue/inject
- Через ф-ю provide передаем data по ключу 'key'
```html
ParentComponent.vue

<script setup>
import { provide } from "vue";

const data = {
	name: 'Alex',
	age: 30
}

provide('key', data)
</script>
```

- В любом дочернем компоненте можем получить доступ
```html
DeepChildComponent

<template>
	<span>{{ data.name }}</span>
</template>

<script setup>
import { inject } from 'vue'
let data = inject('key')
</script>
```