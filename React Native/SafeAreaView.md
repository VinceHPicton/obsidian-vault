
React Native component which can cause choppiness, what it does itstop any content being under the clock or dynamic island etc. Does this with margin/padding/

Better to use 
```
import { useSafeAreaInsets } from "react-native-safe-area-context";
```

