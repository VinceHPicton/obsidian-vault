It measures the width of the character "0" in the font of the element.

This is good because you generally don't each line of text to be longer than 40-75 characters.

This will force the container to have a max-width of 60 x (length of 0 character) and so force text onto new lines after around 60 characters
```
.text-container {
	max-width: 60ch;
}
```
