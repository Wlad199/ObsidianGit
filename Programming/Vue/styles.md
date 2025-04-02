#vue/style
### Использовать Scss
```scss
<style scoped lang="scss">
	.todo {
	  background-color: #fbbe00;
	  &.done {
	    background-color: #55ac6e;
	  }
	}
</style>
```

### Статический и динамический классы
- Статический класс: class="tag" 
- По клику currentTag принмает значение tag
- Динамический класс: :class="{ active: tag === currentTag }">
```html
<button 
	@click="currentTag = tag" 
	v-for="tag in tags" 
	class="tag" 
	:class="{ active: tag === currentTag }">
	{{ tag }}
</button>
```

-  С помощью условного оператора в форме тернарного выражения
```html
<div :class="[transaction.amount > 0 ? 'plus' : 'minus']">
	{{transaction.amount}}
</div>
```
