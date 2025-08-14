```
func main() {

    s := make([]int, 5, 10)

  

    fmt.Println(s)      // [0 0 0 0 0]

    fmt.Println(len(s)) // 5 -> we have 5 actual elements

    fmt.Println(cap(s)) // 10 -> we can allocate up to 10 elements before the underlying array must be reallocated

}
```


- **Length** (`len`) → number of elements the slice currently has.
- **Capacity** (`cap`) → maximum number of elements the slice can hold before it needs to allocate new underlying array space.