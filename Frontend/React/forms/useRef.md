Used to reference values that are not needed for rendering.

Within forms use it to store the value in your <input />'s

It's important to init a useRef with null, otherwise it is undefined which can cause issues.
```
const GenerateAssessmentsContent = () => {
  const nameRef = useRef<HTMLInputElement>(null);

  const handleSubmit = (event: FormEvent) => {
    event.preventDefault();
    if (nameRef.current) console.log(nameRef.current.value);
  };

  return (
    <div>
      <form onSubmit={handleSubmit}>
        <div>
          <label htmlFor="name" className="form-label">
            Name
          </label>
          <input ref={nameRef} id="name" type="text" />
        </div>
        <button type="submit">Submit</button>
      </form>
    </div>
  );
}
```