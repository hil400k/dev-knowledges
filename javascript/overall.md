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

- Rendering starts only after JS processed all calculations.
- JS engine works 'First in - First out'. For example next tasks: 

`dificult scripts is running` → `mouseclick during this time` → `time is off in previously set timeout `. First browser will wait for script calculations → mouseclick handler → timeout callback

- `Macro Tasks` (dom event, timeout), `Micro Tasks` (Promise) are after;
`1 Macro Task` ▸ `All Micro Tasks` ▸ `rendering`
