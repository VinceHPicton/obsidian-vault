- Do not use react context for sharing server state
- Only use it for places where you use useState or useReducer (defining frontend state)
	- Things like currentUser, or selected theme (dark mode/light mode)
![[When to use context and when not to.png]]

Otherwise your component tree will end up like this:
![[When to use context and when not to 2.png]]