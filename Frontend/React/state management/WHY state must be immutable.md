State in react must always be treated as immutable and should only be changed by overwriting it entirely with a new version, [[1a. State and changing it]]

The reason for this is because if you try to edit the state itself, when you return from the  `setXXX()` function, react gets back **the same reference it already had** and therefore concludes nothing has changed, so does not rerender.

TypeScript does physically allow you to edit the state like so:
```
  function FailStateUpdate() {
      setBugs((prevBugs) => {
        prevBugs[0] = {id: 1, title: 'failed', fixed: true};
        return prevBugs
      }
    );
  }
```

But if you do this, **the UI wont reflect the change** when the change happens.

You may think "well I can trigger a re-render later" but that's still wrong, because it will cause weird UI bugs in other ways, since you're breaking a key rule of how the framework expects to work.

So **just don't do it**
