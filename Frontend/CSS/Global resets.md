In index.css you should set
```
*,
*::before,
*::after {
	box-sizing: border-box
}
```
This is explained in [[`box-sizing` property]]

Also:
```
* {
	margin: 0;
	padding: 0;
}
```

Resets and default margin and padding on specific elements