
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