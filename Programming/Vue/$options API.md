``` npm
npm init vue@latest
```
## Base usage

```html
<template>
  <div>
    <h1>Title</h1>
    <p>{{ message }}</p>
    <button @click="userData('my text')" type="button">Submit</button>
  </div>
</template>
```
```js
export default {
  data() {
    return {
      message: "hello world!"
    }
  },
  methods: {
    userData(world) {
      this.message = world
    }
  }
}
```


---
### Отрисовка списков и условное ветвление

```html
<template>
inputs
	<div>
		<input v-model="userName" type="text" placeholder="name">
		<input v-model="userPass" type="text" placeholder="password">
		<input v-model="userEmail" type="text" placeholder="email">
		<button @click="sendData()">Send</button>
	</div>
	<div>

conditionals
		<div v-if="users.length === 0">There are no users</div>
		<div v-else-if="users.length === 1">There is 1 user</div>
		<div v-else="users.length > 1">There are {{ users.length }} users</div>

list
		<ul>
			<li v-for="(el, index) in users" :key="index">
				<p>{{ el.name }}</p>
				<p>{{ el.pass }}</p>
				<p>{{ el.email }}</p>
			</li>
		</ul>
	</div>
</template>
```

```js
export default {
	data() {
		return {
			users: [],
			userName: '',
			userPass: '',
			userEmail: ''
		}
	},
	methods: {
		sendData() {
			this.users.push({
				name: this.userName,
				pass: this.userPass,
				email: this.userEmail
			})
		}
	}
}
```
---


### Отрисовка списка через компонент

- App
```html
<template>
	<div>
		<input v-model="userName" type="text" placeholder="name">
		<input v-model="userPass" type="password" placeholder="password">
		<input v-model="userEmail" type="text" placeholder="email">
		<button @click="sendData()">Send</button>
	</div>
	<ul>
		<User 
			v-for="(el, index) in users" 
			:key="index" 
			:user="el" 
			:index="index" 
			:deleteUser="deleteUser" 
			/>
	</ul>
</template>
```
```js

import User from './components/User.vue'

export default {
	components: { User },

	data() {
		return {
			users: [],
			userName: '',
			userPass: '',
			userEmail: '',
		}
	},
	methods: {
		sendData() {
			this.users.push({
				name: this.userName,
				pass: this.userPass,
				email: this.userEmail
			})
		},
		deleteUser(index) {
			this.users.splice(index, 1)
		}
	}
}
```

- component
```html
	<li>
		<span>{{ user.name }}</span>
		<span>{{ user.pass }}</span>
		<span>{{ user.email }}</span>
		<button @click="deleteUser(index)">delete</button>
	</li>
```
```js
export default {
	props: {
		user: {
			type: Object,
			required: true
		},
		index: {
			type: Number,
			required: true
		},
		deleteUser: {
			type: Function,
			required: true
		}
	}
}
```