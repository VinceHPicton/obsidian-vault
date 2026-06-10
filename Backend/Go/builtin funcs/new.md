Returns a pointer to a zero valued item of given type, allocates memory to it so it's not nil

```
type MyStruct struct {
	name  string
	age   int
	class *string
}

func main() {
	val := new(MyStruct)

	fmt.Println(val) // Output: { 0 <nil>} - empty string, zero, nil ptr
}

```