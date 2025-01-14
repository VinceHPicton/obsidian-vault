Note that axios.get, post, delete, put, and patch and more exist.
```
import axios from "axios"

interface User {
	name: string,
	id: number
}

function AxiosExample() {
	const [users, setUsers] = useState<User[]>([]);
	
	useEffect(() => {
	
	const controller = new AbortController(); // builtin class in browsers
	
	setLoading(true);
	axios.get<User[]>("https://jsonplaceholder.typicode.com/users")
		.then(res => setUsers(res.data))
		.catch((err) => {
			if (err instanceof CanceledError) return;
			console.log(err.message)
		}).finally(() => {
			setLoading(false); // if you wanted a loading spinner
		});

	return () => controller.abort(); // aborts if user navigated away
	}, []) // important to include [] to prevent infinite recalling, since we are setting state  
	
	return (
		<ul>
		{users.map((user) => (
			<li key={user.id}>{user.name}</li>
		))}
		</ul>
	);
}
```

**Using async await instead
- Not recommended as verbose and uses type assertion
```
const [error, setError] = useState("");

useEffect(() => {
	const fetchUsers = async () => {
		try {
			const res = await axios.get<User[]>(
			"https://jsonplaceholder.typicode.com/users"
			);
		  
			setUsers(res.data);
		} catch (err) {
			setError((err as AxiosError).message);
		}
	};
}, []);
```