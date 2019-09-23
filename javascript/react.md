## React

- `render()` will not be invoked if shouldComponentUpdate() returns false.
- `getDerivedStateFromProps` exists for only one purpose. It enables a component to update its internal state as the result of changes in props.
is invoked right before calling the render method, both on the initial mount and on subsequent updates.
- `getSnapshotBeforeUpdate()` to access the DOM before render() new updates. `return ...` from getSnapshotBeforeUpdate() is passed to 
`componentDidUpdate(prevProps, prevState, snapshot)`
- `shouldComponentUpdate()` - invoked before rendering when new props or state are being received.
- `componentDidMount()` called after `render() > getSnapshotBeforeUpdate()`

http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/

- `Controlled components` are inputs that have state controlled be react (setState()). React provides value attr for all inputs besides type=file.
- `Uncontrolled compoents` are components that use `ref` attr to handle updates or to get value

- `Absolute imports`: create `jsconfig.json`
```json
{
  "compilerOptions": {
    "baseUrl": "src"
  },
  "include": ["src"]
}
```

