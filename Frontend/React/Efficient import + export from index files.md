Turn this
```
// index.ts

import TasksProvider from "./TasksProvider";
export { TasksProvider };
```

Into this
```
// index.ts

export { default as TasksProvider } from "./TasksProvider";
```

This says: Take the default export from ./TasksProvider and export it as TasksProvider