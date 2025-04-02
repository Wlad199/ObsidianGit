#vue/fetch #vue/axios

```ts
export const useUserStore = defineStore('userStore', () => {
	const URL = 'https://rqres.in/api/users'
	let users = ref<IUser[]>([])

	const fetchUsers = async () => {
		try {
			const response = await axios.get(URL)
			users.value = await response.data.data
			console.log('success')
		} catch (err) {
			console.warn(err.message)
		}
	}

	onMounted(() => {
		fetchUsers()
	})

	return {
		users,
		fetchUsers
	}
})
```