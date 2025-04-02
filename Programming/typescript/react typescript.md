#react/typescript
#### Children
Существует два распространённых способа описания дочерних элементов компонента. 
Первый — использовать тип React.ReactNode, который является объединением всех возможных типов, которые могут быть переданы в качестве дочерних элементов в JSX:
```ts
	interface ModalRendererProps {
	children: React.ReactNode;
	}
```

Второй - использовать тип React.ReactElement, который включает только элементы JSX, 	а не примитивы JavaScript, такие как строки или числа:
```ts
	interface ModalRendererProps {
		title: string;
		children: React.ReactElement;
	}
```

#### Button
```ts
	type ButtonProps = {
		handleClick: (event: React.MouseEvent<HTMLButtonElement>) => void
	}
```

#### Input
```ts
	type InputProps = {
		value: string,
		handleChange: (event: React.ChangeEvent<HTMLInputElement>) => void
	}
// ИЛИ
	const handleChange: React.ChangeEventHandler<HTMLInputElement> = (e) => {}
```


#### CSS
```ts
	type StyleProps = {
		styles: React.CSSProperties
	}
	const Styles = ({ styles }: StyleProps) => (
			<div style={styles}>
			</div>
			)
```
<Styles styles={{ color: 'green', fontSize: 18, paddingTop: 20 }} />

#### useRef
```ts
const inputRef = useRef<HTMLInputElement>(null)
```