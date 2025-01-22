This is the alternative to using [[useRef]].

```

const GenerateAssessmentsContent = () => {

  const [course, setCourse] = useState("");

  const handleChange = (event: ChangeEvent<HTMLInputElement>) => {
    setCourse(event.target.value);
  };

  return (
	  <form>
		  <label htmlFor="course" className="form-label">
			Select Course
		  </label>
		  <input
			onChange={(event) => handleChange(event)}
			value={course}
			id="course"
			type="text"
		  />
		  <p>{course}</p>
		</div>
		<button type="submit">Submit</button>
	  </form>
  );
};
```
This will allow you to include the value as a piece of state.