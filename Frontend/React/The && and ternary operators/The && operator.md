Logical AND (`&&`) evaluates operands from left to right, returning immediately with the value of the first [falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy) operand it encounters; if all values are [truthy](https://developer.mozilla.org/en-US/docs/Glossary/Truthy), the value of the last operand is returned.


This statement in react:
`{firstVal && secondVal}`
- Evaluates 'firstVal'
- If falsy => returns **the LHS immediately**
- If truthy => evaluates **and returns** secondVal

This is why
`{<p>{mydata}</p> && showDataBool}`
**Always** returns no component, it just returns 'true' if showDataBool is true.

Whereas
`{showDataBool && <p>{mydata}</p>}`
Renders the p tag if showDataBool is true

IMPORTANT
Read [[The problem with && operator]]