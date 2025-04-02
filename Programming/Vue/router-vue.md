### Базовый случай
```html
app.vue

<header>
	<nav>
		<RouterLink to="/">Home</RouterLink>
		<RouterLink to="/about">About</RouterLink>
	</nav>
</header>
<RouterView />

<script>
import { RouterLink, RouterView } from 'vue-router'
</script>
```

```js
// router.js

import { createRouter, createWebHistory } from 'vue-router'
import HomeView from '../views/HomeView.vue'

const router = createRouter({
	history: createWebHistory(import.meta.env.BASE_URL),
	routes: [
		{
			path: '/',
			name: 'home',
			component: HomeView
		},
		{
			path: '/about',
			name: 'about',
			component: () => import('../views/AboutView.vue')
		}
	]
})

export default router
```

```js
// main.js

import { createApp } from 'vue'
import App from './App.vue'
import router from './router/router.js'

const app = createApp(App)
app.use(router)
app.mount('#app')
```