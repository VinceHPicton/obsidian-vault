Done using the reserved "children" prop in React, like this:
```
interface Props {
  children: ReactNode;
}

const MyComponent = ({ children }: Props) => {
  return (
    <div>
      {children}
    </div>
  );
};
```