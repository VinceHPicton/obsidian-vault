`defer` schedules a function call to run **when the surrounding function returns**.

Go guarantees it will run when that function **exits normally or via panic**, but **NOT** if the whole process is forcibly terminated.
```
func f() {
    defer fmt.Println("last")
    fmt.Println("first")
}

// OUTPUT:
first
last
```

Arguments to a deferred function are evaluated **immediately**, not when the defer runs:
```
x := 1
defer fmt.Println(x)
x = 2

// OUTPUT:
1
```


But closures capture variables, so this prints `2`:
```
x := 1
defer func() {
    fmt.Println(x)
}()
x = 2

// OUTPUT:
2
```


Multiple defers run in **last-in, first-out** order:
```
defer fmt.Println("1")
defer fmt.Println("2")
defer fmt.Println("3")

// OUTPUT:
3
2
1
```
