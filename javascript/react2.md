## React Second part

- React component is `pure` if it renders the same output for the same state and props

- Difference between `Component` & `PureComponent` is in default implementation of `shouldComponentUpdate`. It does shallow comparing for props & state.

- It is possible to treat `functional` component as `pure` component using 
```jsx
import React, { memo } from 'react';
...
export default memo(componentName);
```
