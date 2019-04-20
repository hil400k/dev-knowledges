```js
var foo = 10; bar = 3; (function() { var foo = 2; bar = 1; }()); console.info(foo, bar);
// 10, 1
```

### Prototype

```js

const item = {};
item.__proto__ // це і є прототип об'єкту

```
```js
function Parent() {
    this.name = 'name';
}
Parent.prototype.log = function() { console.log(this.name) }
```
> It will set `__proto__` property to Parent.prototype for objects created with new.

> Next code is doing the same
```js
 const item = new Parent();
 item.__proto__.log = function() { console.log(this.name) }
```
> Default prototype object has only one field: constructor - reference to function (Parent)
```js
Parent.prototype → { constructor: Parent }
```
