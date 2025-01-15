1. Lift the state up to the nearest parent (of both current state location and where it's needed)
2. Create a context file for it:
```
interface TasksContextType {
  tasks: Task[];
  dispatch: Dispatch<TaskAction>;
}

// {} as TasksContextType avoids need for having | null in the <>
const TasksContext = React.createContext<TasksContextType>(
  {} as TasksContextType
);

export default TasksContext;
```
3. Wrap component tree using a Provider component, like this:
```
      <TasksContext.Provider value={{ tasks, dispatch }}>
        <NavBar></NavBar>
        <HomePage></HomePage>
      </TasksContext.Provider>
```
4. Use the useContext hook to access the state in value anywhere in the tree:
```
const NavBar = () => {
  const { tasks, dispatch } = useContext(TasksContext);

  return (
    <nav>
      <span>{tasks.length}</span>
    </nav>
  );
};
```