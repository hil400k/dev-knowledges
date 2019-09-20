## React

- `render()` will not be invoked if shouldComponentUpdate() returns false.
- `getDerivedStateFromProps` exists for only one purpose. It enables a component to update its internal state as the result of changes in props.
is invoked right before calling the render method, both on the initial mount and on subsequent updates.
- `getSnapshotBeforeUpdate()` to access the DOM before render() new updates. `return ...` from getSnapshotBeforeUpdate() is passed to 
`componentDidUpdate(prevProps, prevState, snapshot)`
