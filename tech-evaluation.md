### Process:  
- open google sheet form
- start recording before evaluation begins
- fill the sheet
- upload video by the link in ticket

- to check mic + internal volue with `command shift 5`

### html5
types of tags: unpaired, paired, utility tags. 
https://www.toptal.com/html5/interview-questions

new input types: color, date, url, range  

`defer` - script loads on background. If we have 2 scripts with defer and second (by order) is loaded first it will be executed secondly. Order matters.  
`async` - script loads on background. async scripts load in the background and run when ready.  
Both async and defer have one common thing: downloading of such scripts doesn’t block page rendering.  

Meta tags are used to provide useful information to our web pages.  
Title: Provides a title to the web page.
Style: Inserts some styles and CSS details to the web page.
Link: Defines the relationship between one page to another page and an external source.

Improved support for embedding graphics, audio, and video content via the new <canvas>, <audio>, and <video> tags.  
  
```<!DOCTYPE html>``` html5; ```<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">``` html4;   


### CSS  
margin: (top, right, bottom, left).  
box-sizing.  
display: flex.  

```
.center { 
  height: 200px;
  position: relative;
  border: 3px solid green; 
}

.center p {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```
`!important` (is bad or good).  
ways to add CSS to your page (<style>, <link rel...>, style="").  
CSS frameworks.  
z-index.  
pseudo-elements.  
```
@media only screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```
  
### JS.  
ES6 new features: tpl string; Object.assign; let, const; arrow function; class, extend; Destructuring;   

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

Promises  
Arrow function doesn't have bindings to this and super; doesn't have arguments.  

---
Scope.  
```js
if (true) {
  const message = 'Hello';
}
console.log(message); // ReferenceError: message is not defined
```
the same will be with `let`  
please note, that we have `true` and this block is executed anyway  

```js
const i = {
  name: `item${this.age}`,
  age: 11
} 
console.info(i) // // {name: "itemundefined", age: 11}
```

```js
const i = {
  name: function() {
    return `item${this.age}`
  },
  age: 11
}

console.info(i.name()); // item11
```

```js
const i = {
  name: () => {
    return `item${this.age}`
  },
  age: 11
}

console.info(i.name()); // itemundefined
```

```js
const i = {
  name: 'super'
};

i.method = function() {
  console.info(this.name);
}

i.method(); // super
```
> Value of this is defined during code execution
---

Babling & capturing.  

 `event.target` is a particular element where event triggered;  
 `event.currentTarget` is an element where handler is assigned  
 Example: onclick is assigned to parent div; user clicks on any inner element;  
 `event.target` is this element; `event.currentTarget` is always div
 
 3 phases of DOM event: `capturing phase`(from document to particular el)  
  `target phase`(reached the target) `bubbling stage`(from target to document)
  
The only possible ways to turn on capturing are `addEventListener` method with next params:  
`elem.addEventListener(..., {capture: true})`  
`elem.addEventListener(..., true)`  
it can be usefull when you want to do smth before the usual element handler

---



### React

- react component lifecycle
- controlled uncontrolled components
- withRouter func.
- is it possible to pass a value from child to parent?
- React component is `pure` if it renders the same output for the same state and props
- React hooks. `const [count, setCount] = useState(0);` 
```
useEffect(() => {
  document.title = `Ви натиснули ${count} разів`;
}, [count]);
```
only mount and unmount
```
useEffect(() => {
  document.title = `Ви натиснули ${count} разів`;
}, []);
```
- react context
- redux

### Frameworks

The entry (learning) into Angular is tougher than React.  
React doesn’t come with a routing library.  
For React You also need to be familiar with state management libraries like MobX or Redux.  
React doesn't have provided code structure.  
Angular uses real DOM; react uses Virtual DOM; that`s why React is better for freequent updates
Angular: 2-way binding; React: 1-way binding;  

### Data
Local storage, Session storage, Cookies, indexDB.  

Cookies look like a string, you can set key-value pairs with expiration date.  
`document.cookie = "user=John";` rewrites only user cookie  
cookie options are not visible when trying to read cookie 


IndexDB(no size limit)(NoSQL database)  
It can store more than localStorage  
db is a store  
`onupgradeneeded` updates db  
It is possible to add object keys as indexes for search  
Cursors are used to large amount of data

```js
let db;
let dbReq = indexedDB.open('myDatabase', 1);
dbReq.onupgradeneeded = function(event) {
  // Set the db variable to our database so we can use it!  
  db = event.target.result;

  // Create an object store named notes. Object stores
  // in databases are where data are stored.
  let notes = db.createObjectStore('books', {autoIncrement: true});
}

let transaction = db.transaction("books", "readwrite"); // (1)

// get objects store(сховище)
let books = transaction.objectStore("books"); // (2)

let book = {
  id: 'js',
  price: 10,
  created: new Date()
};

let request = books.add(book); // (3)

request.onsuccess = function() { // (4)
  console.log("Book saved to the store", request.result);
};

request.onerror = function() {
  console.log("Error", request.error);
};
```

### Design / Architecture

SOLID  
JavaScript Design Patterns (Basic)
- Singleton
- Adapter
- Composite
- Decorator
- Factory Method
- Mediator  

OOP principles: encapsulation, abstraction, polymorphism, inheritance

MVC. MVP. MVVM.  
MVC MVP difference: View in MVC is not bound to Controller and view is stateless.  
MVC just displays view; MVP comunicates with view through an interface.  
MVVM pattern supports two way data binding between view and view-model.

### CI/CD  

VCS;  

Centralized(CVN) cs Distributed(Git).  

Centralized version control systems are based on the idea that
there is a single “central” copy of your project somewhere 
(probably on a server), and programmers will “commit” 
their changes to this central copy.  

Distributed do not necessarily rely on a central server 
to store all the versions of a project’s files. Instead, 
every developer “clones” a copy of a repository and has the full history 
of the project on their own hard drive. 
This copy (or “clone”) has all of the metadata of the original.
Everything but pushing and pulling can be done without an internet connection.
Actions are fast.  

CI/CD  

CI: 
- npm modules installation
- code check: eslint, tslint ...
- tests
- project build  

CD:  
- deploy to stage
- deploy to production
- tests by qas
  
  Main CI/CD services:  
  Bamboo, Jenkins, Github Actions, Gitlab Actions  
  
Webpack - static module bandler for modern web apps.  
Core items: entry, output, loaders, plugins, mode, browser compatibility.  
`Loaders` allow webpack to process other types (not JS or JSON) of files and convert them into valid modules that can be consumed by your application and added to the dependency graph.  
`Plugins` can be leveraged to perform a wider range of tasks like bundle optimization, asset management and injection of environment variables.  
By setting the mode parameter to either development, production or none, you can enable webpack's built-in optimizations that correspond to each environment.



Merge vs Rebase.  
Merge creates 1 commit for all changes of merged in branch.
Rebase add all commits of merged in branch to master.
```
git checkout bugFix;
git rebase master
```
order of operands is different to 
```
git checkout master
git merge bugFix
```
[https://stackoverflow.com/a/9147389/4675980]

### Networks

dns.  
cors.  
- simple (get, post, head)
- not simple (put, delete ...)

> Browser asks server for permission to do some request: Option request with a deteils of request that should be sent:
Access-Control-Request-Method & Access-Control-Request-Headers (not simple requests).

> Browser automatically adds header `Origin` with a url of website to the request. Server should add `Access-Control-Allow-Origin` to response headers if it allows this request. if there are no such header, browser will understand this response as an error.

> Server sends `Access-Control-Allow-Origin` with value (url of a website from which this request was sent) if server allows to send CORS.

> Use `withCredentials` header to send cookies and http authorazation to ask access.
web-sockets - is a protocol that provides a way of exchanging data between browser and server in persistent connection. Data passed  
as a packets.

WebSocket  
```
let socket = new WebSocket("wss://javascript.info/article/websocket/demo/hello");

socket.onopen = function(e) {
  alert("[open] Connection established");
  alert("Sending to server");
  socket.send("My name is John");
};

socket.onmessage = function(event) {
  alert(`[message] Data received from server: ${event.data}`);
};

socket.send({smth: true})
```
http statuses:
1×× Informational
2×× Success
3×× Redirection
4×× Client Error
5×× Server Error

### Security

Authorization & Authentication. JWT. XSS. CSRF.

OAuth - is an open standard for authorization  

4 modes are available: 1) back + front configurations 2) front only configuration 3) not provider (Google, etc.) email and password 4)  
Security: The answer is, unquestionably, NO! OAuth2 is NOT (inherently) SECURE. Numerous, well-known security issues with the protocol that have yet to be addressed.  

OAuth Central Components:
- Scopes and Consent: Permissions. Scopes are what you see on the authorization screens when an app requests permissions. They’re bundles of permissions asked for by the client when requesting a token.
- Actors: The actors in OAuth flows are as follows:
  1. Resource Owner: owns the data in the resource server. For example, I’m the Resource Owner of my Facebook profile.
  2. Resource Server: The API which stores data the application wants to access
  3. Client: the application that wants to access your data
  4. Authorization Server: The main engine of OAuth
- Clients: devices, 
- Tokens
- Authorization Server
- Flows
 
Cross-Site Request Forgery (CSRF) — CSRF is an attack that tricks the victim into submitting a malicious request.  
Cross-Site Scripting (XSS) Attack — XSS is a type of attack in which an attacker inputs a malicious script into the web application.  
DOS (Denial Of Service) Attack — DOS attack is a cyber-attack in which a perpetrator seeks to make a server resource unavailable to the actual users by disrupting the services of a server connected to the internet.  

### Cloud

Cloud services:  
Examples: Amazon S3, Amazon Lambda, Amazon Glacier, Amazon SNS, Amazon Cloudfront.  
Cloud refers to a distinct IT environment that is designed for the purpose of remotely provisioning IT resources  
Cloud Computing Models: Infrastructure as a Service (IaaS), Platform as a Service (PaaS),
Software as a Service (SaaS)  
SaaS: Google docs, Gmail, Google drive  
PaaS(programming language execution env, OS, Web Server, Database):
Amazon Elastic, Heroku, windows azure, 
IaaS(CPU, GPU, Data Storage, Servers & Network): Amazon EC2

### Testing

Unit testing, test-coverage, spy, karma, jest, jasmine, mock
  
Types of testing:  
> Unit-tests.  

> Integration tests. (Integration tests verify that different modules or services used by your application work well together).  

> Functional tests. (Functional tests focus on the business requirements of an application. They only verify the output of an action and do not check the intermediate states of the system when performing that action).  

> End-to-end tests. (End-to-end testing replicates a user behavior with the software in a complete application environment. It verifies that various user flows work as expected and can be as simple as loading a web page or logging in or much more complex scenarios verifying email notifications, online payments, etc).  

> Acceptance testing. (Acceptance tests are formal tests executed to verify if a system satisfies its business requirements).  

> Performance testing. (Performance tests check the behaviors of the system when it is under significant load).  

> Smoke testing. (Smoke tests are basic tests that check basic functionality of the application. They are meant to be quick to execute, and their goal is to give you the assurance that the major features of your system are working as expected).  

### JS Code Quality & Best Practices 

lint, refactoring, static type checking: typescript  

### Processes

scrum

General understanding of SDLC(Systems Development Life Cycle) model.  
Models: Agile, Waterfall, Spiral, V-shaped, Iterative

