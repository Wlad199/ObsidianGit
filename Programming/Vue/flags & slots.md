### Условный рендеринг при активном флаге
#vue/flag
- Два дочерних компонента будут по разному рендериться в зависимости от флага: :canShowButton
```html
app.vue

<template>
	<child-component :text="text" :button="button"></child-component>
	<child-component :text="text" :button="button" :canShowButton="true"></child-component>
</template>

<script>
	data() {
		return {
			title: 'This is title',
			text: 'This is text',
			button: 'This is button',
			canShowButton: false
		}
	}
}
</script>
```
```html
ChildComponent.vue

<template>
	<p>{{ text }}</p>
	<button v-show="canShowButton">{{ button }}</button>
</template>

<script>
export default {
	props: {
		text: String,
		button: String,
		canShowButton: {
			type: Boolean,
			default: false
		}
	}
}
</script>
```

### Слоты
#vue/slot 
- Слоты синхронизируются по именам
- Родитель: `v-slot:text`  Потомок: `name="text"`
- v-slot:text и `#text` идентичны
- `<slot>` без `name` неявно имеет имя "default"
- `v-slot:default` - Значение по-умолчанию
- `<p v-if="$slots.text"><p>` отрендерится  если будет передан родителем `v-slot:text`
```html
app.vue

<template>
	<child-component>
		<template v-slot:text>This is text</template>
		<template #button>this is button</template>
		<template v-slot:default>default text</template>
	</child-component>
	<child-component>
		<template v-slot:default>This is text</template>
	</child-component>
</template>
```
```html
ChildComponent.vue

<template>
	<div>
		<p v-if="$slots.text">
			<slot name="text" />
		</p>
		<button v-if="$slots.button">
			<slot name="button" />
		</button>
		<span v-if="$slots.default">
			<slot />
		</span>
	</div>
</template>
```