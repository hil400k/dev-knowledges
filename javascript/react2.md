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
- `HOC` can be used to as a decorator (or wrapper) that gives some additional logic to some component.
For example we have few components that should have subscribe/unsubscribe.
- `HOF` is a function that takes function as a param, returns function or both cases together.

- Simple use case fur `render` prop
```jsx
...
render() {
    return (
      <div>
        <Parent render={({name}) => (<Child name={name} /> )} />
      </div>
    );
  }
...
```
Parent.js
```jsx
import React from 'react';

export default (props) => {
  return props.render({ name: 'SuperName' }); 
};
```
Child.js
```jsx
import React from 'react';

export default ({ name }) => {
  return (
    <h1>
      {name} !!!
    </h1>
  );
};
```
► Result: ```<h1>SuperName !!!</h1>```

---

### Redux

> `store.subscribe()`

> Ways to copy array: `someArr.filter(result => true);` `[...someAee]`

> To get value in reducer from another reducer, you should pass it within
> action object ({ type: 'SOME_TYPE', data: 'HERE!!!!' } }) from a component

> `(dispatch, getState) => { getState(); ... }` function to get current state 

---

> `Middleware structure`
```jsx
const logger = store => next => action => {
  console.log('dispatching', action)
  let result = next(action)
  console.log('next state', store.getState())
  return result
}
```
We have 2 returned functions because it allows chaining and dispatch accumulating function;
```jsx
{
  const store = {
    dispatch(action) {
      return action;
    },
    getState() {
      return 'state';
    }
  };

  function logger2(store) {
    return function wrapDispatchToAddLogging(next) {
      return function dispatchAndLog(action) {
        console.log('dispatching', action)
        let result = next(action)
        return result
      }
    }
  };

  function logger3(store) {
    return function wrapDispatchToAddLogging(next) {
      return function dispatchAndLog(action) {
        console.log('dispatching2', action)
        let result = next(action)
        return result
      }
    }
  }

  let point = logger2(store)(store.dispatch);
  let point2 = logger3(store)(point)('he');
}
```
> Output `dispatching2 he` `dispatching he`. It is because `dispatch` (next()) accumulates logic (becomes bigger) after each call and it is passed already improved to next middlware.

> Check inner components render after parent shouldComponentUpdate
Checked: inner component render doesn't run if outer component shouldComponentUpdate returns false
