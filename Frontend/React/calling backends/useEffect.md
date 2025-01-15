```
useEffect(() => {
	fetch("https://api.imgflip.com/get_memes")
	.then(res => res.json())
	.then(data => console.log(data))
}, [dependency1, dependency2])
```

- Dependencies can be props or state
- Basically allows you to call some external thing if a dependency changes, also runs when component renders
- function callback can never be an async function


- If you omit the dependencies, it would be better named as "afterRender," as it will run after every render.
	- This is why you get into an infinite loop of calling the given callback if any state is changed within the callback. The function causes a state change - this causes a rerender, and this causes the function to run again...
	- You can prevent this by passing an empty array as dependencies.


**The cleanup function**
```
useEffect(() => {
	connectDB();
	
	return () => disconnectDB();
})
```
- You can set a return as another callback to cleanup after useEffect runs. This will be the thing that resets anything, like closing modals etc, that the useEffect caused.