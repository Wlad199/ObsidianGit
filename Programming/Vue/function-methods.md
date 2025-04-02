### Использование методов вместо ф-ий
#vue/function #vue/methods
- Через ф-ии
```html
<AssignmentList :assignments="inProgress" title="In Progress" />
<AssignmentList :assignments="completed" title="Completed" />

<script>
export default {
	computed: {
		inProgress() {
			return this.assignments.filter(assignment => !assignment.completed)
		},
		completed() {
			return this.assignments.filter(assignment => assignment.completed)
		}
	}
}
</script>
```

- Через методы
```html
<template>
	<AssignmentList :assignments="filters.inProgress" title="In Progress" />
	<AssignmentList :assignments="filters.completed" title="Completed" />
</template>

<script>
export default {
	computed: {
		filters() {
			return {
				inProgress: this.assignments.filter(assignment => !assignment.completed),
				completed: this.assignments.filter(assignment => assignment.completed)
			}
		}
	}
}
</script>
```