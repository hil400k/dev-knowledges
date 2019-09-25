## React Second part

- React component is `pure` if it renders the same output for the same state and props

- Difference between `Component` & `PureComponent` is in default implementation of `shouldComponentUpdate`. It does shallow comparing for props & state.

- It is possible to treat `functional` component as `pure` component using 
```jsx
import React, { memo } from 'react';
...
export default memo(componentName);
```
- `render={...}` prop of the component
```jsx

class Cat extends React.Component {
  render() {
    const mouse = this.props.mouse;
    return (
      ...
    );
  }
}

class MouseTracker extends React.Component {
  render() {
    return (
      <div>
        <h1>Move the mouse around!</h1>
        <Mouse render={mouse => (
          <Cat mouse={mouse} />
        )}/>
      </div>
    );
  }
}

class Mouse extends React.Component {
...
  render() {
      return (
        {this.props.render(this.state)}
      )
  }
}
```