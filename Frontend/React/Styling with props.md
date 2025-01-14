```
import styles from "./Button.module.css";

interface Props {
children: string;
colour?: "primary" | "secondary" | "danger";
onClick: () => void;
}

const Button = ({
onClick: handleClick,
children,
colour = "primary",
}: Props) => {
	return (
	<button
	className={[styles.btn, styles["btn-" + colour]].join(" ")}
	onClick={handleClick}
>					
		{children}
	</button>
	);
};

export default Button;
```