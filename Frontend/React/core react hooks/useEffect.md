useEffect  exists to allow a React component to perform **side effects**

It's react mechanism for saying "after you finish rendering, run this piece of code"

```
useEffect(() => {
  console.log("code here is run after rendering");
}, [dependency1, dependency2]);
```

useEffect always runs after the initial component render, and then only runs again if any of it's **dependencies** change.

This means a common pattern looks like:
```
useEffect(() => {
  fetchUsers().then(setUsers);
}, []);
```
This useEffect has no dependencies, so it will fetch users on initial render, and then won't ever run again. 
Importantly, if you omit the [] it will still trigger the infinite rerender loop below (tested this myself).


# Why do we need to use useEffect to do the initial fetch? What happens if we don't?

In short, you would get into an infinite re-rendering loop

Let's say you put
`fetchUsers().then(setUsers);` 
into your react component function.

React would
- render
- call `fetchUsers`
- then call `setUsers`
- which would cause rerender (as the component function runs again)
- thereby triggering a fetch again
- thereby calling `setUsers` again
- and so on forever

So `useEffect` solves the problem of:

> “Run this after render, but only when dependencies change.”