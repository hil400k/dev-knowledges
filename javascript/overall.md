```js
var foo = 10; bar = 3; (function() { var foo = 2; bar = 1; }()); console.info(foo, bar);
// 10, 1
```

### Prototype

> All JavaScript objects inherit properties and methods from a prototype.

> Date objects from Date.prototype

> Array objects from Array.prototype

> Date objects, Array objects inherit from Object.prototype.

```js

const item = {};
item.__proto__ // this is the prototype

```
```js
function Parent() {
    this.name = 'name';
}
Parent.prototype.log = function() { console.log(this.name) }
```
> It will set `__proto__` property to Parent.prototype (const o = new Parent(); o.__proto__ === ...prototype) for objects created with new.

> Next code is doing the same
```js
 const item = new Parent();
 item.__proto__.log = function() { console.log(this.name) }
```
> Default prototype object has only one field: constructor - reference to function (Parent)
```js
Parent.prototype → { constructor: Parent }
```
---
---
---
- Rendering starts only after JS processed all calculations.
- JS engine works 'First in - First out'. For example next tasks: 

`dificult scripts is running` → `mouseclick during this time` → `time is off in previously set timeout `. First browser will wait for script calculations → mouseclick handler → timeout callback

- `Macro Tasks` (dom event, timeout), `Micro Tasks` (Promise) are after;
`1 Macro Task` ▸ `All Micro Tasks` ▸ `rendering`

- При наступлении события обработчики сначала срабатывают на самом вложенном элементе, затем на его родителе, затем выше и так далее, вверх по цепочке вложенности. Например, есть 3 вложенных элемента `FORM > DIV > P`, с обработчиком на каждом. Если кликнуть на P, то последовательно выведутся alert: `p → div → form`. Самый глубокий элемент, который вызывает событие, называется «целевым» или «исходным» элементом и доступен как event.target. `event.stopPropagation()`

### Programming paradygms
>Imperative programming focuses on describing how the program works.

>Declarative is a little flexible in that it works by telling the program what it should accomplish without specifying how the program is to achieve it.
- Imperative way. When using an imperative pattern, there is an exact procedure that the program needs to take in order to produce the correct output. 
```js
let ticketSales = [
   {name:'Twenty One Pilots', isActive: true, tickets:430}, 
   {name:'The Wiggles Reunion', isActive: true, tickets:257},
   {name:'Elton John', isActive: false, tickets:670}
]
/*using imperative*/
let activeConcerts = [];
for (let i = 0; i < ticketSales.length; i++){
    let t = ticketSales[i]; 
    if(t.isActive){ 
    activeConcerts.push(t)
  }
}
```
- Declarative
```js
/*using declarative style of coding using the same data*/
let activeConcerts = [];
activeConcerts = (ticketSales.filter((t)=>{
   return t.isActive;
}))
```

### Date
- Convert date to ISO format: `new Date('07/29/2019 04:00:00').toISOString();`
- Current date to ISO format: `new Date().toISOString()`
- Convert date to UTC (date is the same but more readable format): `new Date('07/29/2019 04:00:00').toUTCString();`
- `new Date()` always returns date in current timezone, even when we pass UTC/ISO string

### async/await
- `await` is possible to set only within async functions
- `await` waits for result of promise after operator, example `let result = await promise`
- `async` guaranties that function will return a promise

```js
(async function() {
  const af = async () => {
    const result = await new Promise(resolve => {
      setTimeout(() => resolve(10), 1000);
    });

    return result;
  }

  af().then(console.log);
})();
```
it will return `10`

### CORS
- simple (get, post, head)
- not simple (put, delete ...)

> Browser asks server for permission to do some request (not simple requests)

> Server sends `Access-Control-Allow-Origin` with value (url of a website from which this request was sent) if server allows to send CORS.


