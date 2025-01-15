```
interface User {
	name: string,
	id: number
}

function MyComponent() {
	const [users, setUsers] = useState<User[]>([]);
	
	return <div></div>
}
```