### Утверждение типов
- Для объектов
```ts
let state = ref({
	name: 'Alex',
// Утверждение типов
	age : 28 as string | number
}) 
state.value.age = '30'
// или
import Job from '../types/job.ts'
const jobs = ref<IJob[]>([])
```
- Для примитовов
```ts
let firstName = ref<number | string>('Anna')
firstName.value = 56
// или
import { Ref } from 'vue';
const name:Ref<string> = ref('Alex')
```
### Утверждение пропсов
- Через PropType
```ts
import Job from '../types/job.ts'
import { PropType } from 'vue';

const props = defineProps({
	jobs: {
		required: true,
		type: Array as PropType<Job[]>
	}
})
```
- Через дженерики
```html
// App.vue

<div>
	<JobList 
		:name="name" 
		:message="message"
	/>
</div>
<script setup lang='ts'>
	const name:Ref<string> = ref('Alex')
	const message = ref<string>('Hello!!!')
</script>

```
```html
// Children.vue

<div>
	<p>{{ props.message }}</p>
	<p>{{ props.name }}</p>
</div>
<script setup lang="ts">
	const props = defineProps<{
		message: string,
		name: string
	}>()
</script>
```
### Утверждение Emits
```html
Children.vue

<div>
	<button @click="sendData">click me</button>
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

### event
```js
function handleChange(event: Event) {
  console.log((event.target as HTMLInputElement).value)
}
```
