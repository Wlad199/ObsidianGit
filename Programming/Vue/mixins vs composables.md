### Миксин
#vue/mixin
```js
// mixins/flash.js

import swal from "sweetalert"

export default {
	methods: {
		flash(message) {
			return swal('Success!', message, 'success')
		}
	}
}
```

```html
component.vue

<template>
	<button @click="flash('Hello')">click</button>
</template>

<script>
import flash from '../mixins/flash.js'

export default {
	mixins: [flash]
}
</script>
```

### Композиция 
#vue/composables 
```js
// composables/useFlash.js

import swal from "sweetalert"

export function useFlash() {
	function flash(message) {
		return swal('Success!', message, 'success')
	}
	return { flash }
}
```
```html
component.vue

<template>
	<button @click="flash('Hello')">click</button>
</template>

<script setup>
	import { useFlash } from '../composables/useFlash.js'
	let { flash } = useFlash()
</script>
```