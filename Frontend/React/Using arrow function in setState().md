In the following scenario we have 2 options: 
```
const [expand, setExpand] = useState(false);

const toggleExpand1 = () => {
	setExpand((prev) => !prev);
};

const toggleExpand2 = () => {
	setExpand(!expand);
};
```

The right way is toggleExpand1, because this ensures you are always working with the **most current state**

React’s `useState` updates are **asynchronous** and **batched**. If you call `setExpand(!expand)` (like in `toggleExpand2`), you’re relying on the current value of `expand`, which **might not be up-to-date** due to how React batches state updates.

Basically because if you spam the toggle button fast enough option 2 could go wrong.