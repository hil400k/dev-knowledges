```js
var foo = 10; bar = 3; (function() { var foo = 2; bar = 1; }()); console.info(foo, bar);
// 10, 1
```
