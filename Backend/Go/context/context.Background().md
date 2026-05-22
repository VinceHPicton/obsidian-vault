`context.Background()` is basically:

- an empty root context
- never cancelled
- no timeout
- no values

Think of it as the “origin” of a context tree.

# When do you use `Background()`?

Usually only at:

- application entry points
- tests
- `main()`
- initial goroutine setup

Example:

```
func main() {    ctx := context.Background()}
```

or:

```
func TestSomething(t *testing.T) {    ctx := context.Background()}
```

---

# In servers, you usually DON'T use Background()

Because frameworks already give you a parent context.

HTTP example:

```
func handler(w http.ResponseWriter, r *http.Request) {    ctx := r.Context()}
```