### Base
```html
<template>
	<p>About Page</p>
	<p>{{ message }}</p>
	<input v-model="message" type="text">
</template>

<script setup>
import { onMounted, ref } from "vue"

let message = ref('this is message')
onMounted(() => {
	message.value = 'new message'
})
setTimeout(() => {
	message.value = 'another message'
}, 1000)
</script>
```