
#vue/emit
```html

ChildrenComponent.vue

<template>
	<button @click="sendData">Send</button>
</template>

<script setup>
// Инициализировать emit и объявить передаваемый сигнал
const emit = defineEmits(['sendAmount'])

// Данные для отправки
const amount = 30

const sendData = () => {
// При клике передать в emit название сигнала и данные
	emit('sendAmount', amount)
	console.log('signal sent');
}
</script>
```
```html
App.vue

<template>
// Название события равно названию сигнала
<ChildrenComponent @sendAmount="handlerSendAmount"/>
</template>

<script setup>
import ChildrenComponent from './components/ChildrenComponent.vue';

// Обработка полученых данных
const handlerSendAmount = (amount)=> {
	console.log(amount);
}
</script>
```

### Утверждение Emits
```html
Children.vue

<div>
	<button @click="transferData">click me</button>
</div>

<script setup lang="ts">
	const name = 'Alex'
	const age = 32

// Без типизации:
	const emit = defineEmits(['sendData'])

// С типизацией (способ 1)
	const emit = defineEmits<{
		(e: 'sendData', inner: string): void
	}>() 

// С типизацией (способ 2)
	const emit = defineEmits<{
		sendData: [name: string, age: number]
	}>()

	const transferData = () => {
		emit('sendData', name, age)
	}
</script>
```
```html
App.vue

<div>
	<Children @sendData="hanleSendData"	/>
</div>

<script setup lang='ts'>
	const hanleSendData = (name: string, age: number) => {
		console.log(name, age)
	}
</script>
```

### Удалить из потомка
```html
Children

<button @click="$emit('deleteUser', user.id)">delete</button>
```
```html
App

<template>
    <UserList
      v-for="user in users"
      :user="user"
      @deleteUser="handlerDeleteUser" />
</template>


<script setup lang='ts'>
const handlerDeleteUser = (id: number) => {
    users.value = users.value.filter(user => user.id !== id)
}
</script>
```

### Счетчик
```html
App.vue

<template>
	<div>{{ count }}</div>
	<ChildComp @change="changeHandler" />
</template>

<script lang="ts" setup>
const count = ref<number>(0)

const changeHandler = (amount: number) => {
	count.value = count.value + amount
}
</script>
```
```html
ChildComp.vue

<template>
  <button @click="$emit('change', 1)">Plus</button>
  <button @click="$emit('change', -1)">Minus</button>
</template>
```