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
### How does JS works
- Rendering starts only after JS processed all calculations.
- JS engine works 'First in - First out'. 
`FIFO: oldest item is in the front of the queue. 
When an item needs to be replaced, item in the front of the queue is selected for removal`
For example next tasks: 

`dificult scripts is running` → `mouseclick during this time` → `time is off in previously set timeout `. 
First browser will wait for script calculations → mouseclick handler → timeout callback

- `Macro Tasks` (dom event, timeout), `Micro Tasks` (Promise) (are after `Macro Task`;
Sequence is next: `1 Macro Task` ▸ `All Micro Tasks` ▸ `rendering`

Є черга в яку записуються всі задачі (макро таски): допустимо зараз виконується якийсь скрипт,
під час цього користувач клікнув десь, браузер запише подібю в чергу (вона виконається тільки 
після того як браузер завершить попереднє завдання) (те ж само буде з таймаутом). Скрипт, Івент, 
Таймаут - це макротаски. Після кожного виконання макротаску запускається виконання черги 
всіх мікротасків (проміси). Тільки після цього запускається рендерінг

- При наступлении события обработчики сначала срабатывают на самом вложенном элементе, затем на его родителе, затем выше и так далее, вверх по цепочке вложенности. Например, есть 3 вложенных элемента `FORM > DIV > P`, с обработчиком на каждом. Если кликнуть на P, то последовательно выведутся alert: `p → div → form`. Самый глубокий элемент, который вызывает событие, называется «целевым» или «исходным» элементом и доступен как event.target. `event.stopPropagation()`
---
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

> Browser asks server for permission to do some request: Option request with a deteils of request that should be sent:
Access-Control-Request-Method & Access-Control-Request-Headers (not simple requests).

> Browser automatically adds header `Origin` with a url of website to the request. Server should add `Access-Control-Allow-Origin` to response headers if it allows this request. if there are no such header, browser will understand this response as an error.

> Server sends `Access-Control-Allow-Origin` with value (url of a website from which this request was sent) if server allows to send CORS.

> Use `withCredentials` header to send cookies and http authorazation to ask access.


### Patterns

- Factory pattern is needed in cases when you want to have a control on creation of objects. For example to have a possibility to add some param or calculations for all objects before creating.

- Abstract Factory is a controller for another Factories. It will use required factory depended on requirements.
```js
function AbstractFactory(type) {
    return type === 'small' ? SmallFactory() : largeFactory();
}

// type is small | large
```

---
---
### Rx.js
- shareRaplay is an operator that is used to not create separate stream for eahc subscriber.
It is to use shared one. Useful to handle 2 async pipes for one request. In result app will send only one.
