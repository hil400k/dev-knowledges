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
- `@import-normalize;` can be controlled via browserlist in package.json
- To add `.svg`
```jsx
import { ReactComponent as Logo } from './logo.svg';
const App = () => (
  <div>
    {/* Logo is an actual React component */}
    <Logo />
  </div>
);
```
- Composition example:

```jsx
function Page(props) {
  const user = props.user;
  const userLink = (
    <Link href={user.permalink}>
      <Avatar user={user} size={props.avatarSize} />
    </Link>
  );
  return <PageLayout userLink={userLink} />;
}

// Now, we have:
<Page user={user} avatarSize={avatarSize} />
// ... which renders ...
<PageLayout userLink={...} />
// ... which renders ...
<NavigationBar userLink={...} />
// ... which renders ...
{props.userLink}
```
- `Context.Provider`
```jsx
<MyContext.Provider value={/* some value */}>
class MyClass extends React.Component {
  componentDidUpdate() {
    let value = this.context;
  }
}

MyClass.contextType = MyContext;
```
For function components
```jsx
<MyContext.Consumer>
  {value => /* render something based on the context value */}
</MyContext.Consumer>
```
Context objects should be created using 
`React.createContext({})`

- ```jsx
<input type="text"  defaultValue="some val" ref={this.input} /> 
``` Default value props exists for uncontrolled components to have possibility to set default value. If to set just value it willn't have a possibility to change a value of input
