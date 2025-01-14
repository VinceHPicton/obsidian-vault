How to useState in react
const [count, setCount] = React.useState(0)

All pieces of state should be treated as **immutable** ie you can only "change" them by completely overwriting them in the useState set function.

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


**Object**
Create a new object using the spread operator, and update the field(s) you wanna change
```
const [drink, setDrink] = React.useState({
	name: "latte",
	price: 5,
	size: "L"
})
function updatePrice() {
	setDrink({
		...drink,
		price: 6
	})
}
```

**Nested object**
The spread operator in JS is shallow - meaning if you did the same as above normal object, the new object would share a reference to the old object, this means you have to do the spread operator within the nested object, as below, and that's why **it's best to avoid nested objects as state**
```
const [customer, setCustomer] = React.useState({
	name: "Vince",
	age: 27,
	address: {
		number: 70,
		postcode: "BS167DW",
		city: "Bristol"
	}
})
function updateAddress() {
	setCustomer({
		...customer,
		address: {
			...customer.address,
			postcode: "BS154JH"
		}
	})
}
```

**Array**
The correct way to change an array state is to provide a whole new array:
```
const [items, setItems] = React.useState([])
function addNewItem() {
	setItems(prev => [...prev, "NewItem"])
}
```
You can't use `setItems(prev => prev.push("NewItem"))` for a few reasons, but primarily it just doesn't work - .push() does not return the new array, it returns the length, so it doesn't even set the new state.

**array of objects**

```
const [bugs, setBugs] = React.useState([
	{ id: 1, title: 'Jira ticket 1', fixed: false},
	{ id: 2, title: 'Jira ticket 2', fixed: false}
])
function fixBug1() {
	setBugs(bugs.map(bug => bug.id === 1 ? { ...bug, fixed: true } : bug))
}
```