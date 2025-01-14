```
function handleChange(event) {
	const {value} = event.currentTarget
	console.log(value)

	setVal(event.currentTarget.value)
}
```

```
<input
	onChange={handleChange}
/>
```

As a user typed "text" into the input, console log would show:
> t
> te
> tex
> text

=> currentTarget is innerHTML?

How to make the react state follow the exact current text followed - making it a controller component
```
<input
	onChange={handleChange}
	value={stateVar}
/>
```