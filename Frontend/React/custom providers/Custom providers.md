These can be used to clean up reducer code like this
```
function App() {
  const [tasks, taskDispatch] = useReducer(taskReducer, []);

  const [user, userDispatch] = useReducer(userReducer, "");

  return (
    <AuthContext.Provider value={{ user: "", userDispatch: userDispatch }}>
      <TasksContext.Provider value={{ tasks, dispatch }}>
        <NavBar></NavBar>
        <HomePage></HomePage>
      </TasksContext.Provider>
    </AuthContext.Provider>
  );
}
```
Problems:
- The keyword dispatch can't be used more than once, so we end up having to name dispatches eg taskDispatch, userDispatch
- Messy HTML

**Solution**
Create a custom provider component:
```
interface Props {
  children: ReactNode;
}

const AuthProvider = ({ children }: Props) => {
  const [user, dispatch] = useReducer(userReducer, "");

  return (
    <AuthContext.Provider value={{ user, dispatch }}>
      {children}
    </AuthContext.Provider>
  );
};

export default AuthProvider;
```

Cleanup the place where it's used:
```
function App() {
  const [tasks, dispatch] = useReducer(taskReducer, []);

  return (
    <AuthProvider>
      <TasksContext.Provider value={{ tasks, dispatch }}>
        <NavBar></NavBar>
        <HomePage></HomePage>
      </TasksContext.Provider>
    </AuthProvider>
  );
}
```