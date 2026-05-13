Immer has essentially 1 job: let you write mutable-style state updates in react, whereas in vanilla you can't. [[WHY state must be immutable]]

### What does this mean exactly?
Well in react normally, when you edit state with the `setX()` func from useState, you must always pass in an entirely new string/object/array/whatever to overwrite the old state with.

This means that if you wanted to change the state of a complex  nested object, your code becomes rather a mess, since you can't just edit the 1 field you need to change:
```
setState(prev => ({
  ...prev,
  user: {
    ...prev.user,
    settings: {
      ...prev.user.settings,
      theme: "dark"
    }
  }
}));
```
Here we just wanted to change theme to "dark" but we had to write all that other shit to create a whole new object.


But with `produce()` from immer, we can treat a "draft" object as mutable and return it, making the above update just:
```
setState(produce(draft => {
  draft.user.settings.theme = "dark";
}));
```
