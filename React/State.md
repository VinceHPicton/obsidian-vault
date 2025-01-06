How to useState in react
const [count, setCount] = React.useState(0)

If you ever need the old value of state to help you determine the new value of state, you should pass a callback function to your state setter function instead of using state directly. This callback function will receive the old value of state as its parameter, which you can then use to determine your new value of state.

```
function add() {
	setCount(prevCount => prevCount + 1)
}
```



If you don't care about the old value at all, we provide a new value.

```
function makeCount1000() {
	setCount(1000)
}
```



The correct way to change an array state is to provide a whole new array:

```
const [items, setItems] = React.useState([])
function addNewItem() {
	setItems(prev => [...prev, "NewItem"])
}
```
You can't use `setItems(prev => prev.push("NewItem"))` for a few reasons, but primarily it just doesn't work - .push() does not return the new array, it returns the length, so it doesn't even set the new state.

