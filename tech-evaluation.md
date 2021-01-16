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
  
# Webpack - ?  
Merge vs Rebase.  
Merge creates 1 commit for all changes of merged in branch.
Rebase add all commits of merged in branch to master.
[https://stackoverflow.com/a/9147389/4675980]

### Networks

# dns, cors, web-sockets, http?

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

# General understanding of SDLC model?

