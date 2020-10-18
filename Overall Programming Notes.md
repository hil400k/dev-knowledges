# Overall Programming Notes

<details>
<summary>OOP Principles</summary>
 1) Encapsulation (Private, Public, Protected)
 2) Inheritance
 3) Polymorphism (Possibility to override methods with a same name in child classes)
</details>

### Facade Pattern TS

```ts
// забезпечує новою інформацією
class NewsProvider {
  getNews() {}
}
// Відображає
class NewsPresenter {
  present() {}
}
// Підготовлює до відображення
class NewsEditor {
  prepare() {}
}
// Розподіляє по категоріях
class NewsRouter {
  setToCateggory() {}
}

// Об'єднує декілька сутностей для сумісного виконання команди
class NewsFacade {
  provider;
  editor;
  presenter;
  router;

  constructor(
    private inputProvider,
    private inputEditor,
    private inputPresenter,
    private inputRouter
  ) {
    this.provider = inputProvider;
    this.editor = inputEditor;
    this.presenter = inputPresenter;
    this.router = inputRouter;
  }

  runNews() {
    this.provider.getNews();
    this.editor.prepare();
    this.router.setToCateggory();
    this.presenter.present();
  }
}
```

> Use online tests before interview

> MAC OS give full permissions for folder `sudo chmod 777 folder-name`

> sudo pkill -9 ng node npm (kill all node processes)

> open -a telegram; open -a skype; open -a webstorm; open -a chrome (MAC command to run few app in one time from terminal)

> `cd ~/; nano .bash_profile` `alias add-alias="cd ~/; nano .bash_profile"` TO Add New Alias Command To Add Aliase

> USE NANO EDITOR FROM TERMINAL

> TERMINAL: you can combine commands with `&&` or `;`

> Open Webstorm project from terminal: open -a /Applications/WebStorm.app `here should be folder path`

> <strong>Mac Set Screenshot hotkeys: alt + 3 copy selected area to clipboard</strong>

> <strong>Mac Set Screenshot hotkeys: alt + 4 save selected area as a file</strong>

---

HTTP/HTTPS(encrypted) - protocols

```
HTTPS: request a page: request to the server -> 
agreement between the web browser and web server about how to encrypt the data (handshake):
    Web server sends SSL certificate (with public key) to the browser -> 
    Browser sends certificate verified message to server
Browser generates symmetric key and encrypts it using public key (key from the server) ->
Browser sends this encrypted symmetric key to the server -> 
This encrypted key is used for entire session.
```

> Symmetric key means that we need the same key to encrypt and decrypt. Asymmetric is opposite.
> ssl makes sure that data between two systems is imposible to read.

---

Http headers examples: `WWW-Authenticate` `Authorization` `Accept`
`Keep-Alive` `Cookie` `Content-Type`

---

SOLID
- single responsibility
- open/closed open for extension closed for modification
- liskov substitution: objects can be replaced with their extended objects without code change
- interface segregation. better to have more interfaces than one large
- dependency inversion: top level modules are independed from low level modules.
Abstractions are not depended of details. Details depended of abstractions.  
https://medium.com/webbdev/solid-4ffc018077da


---
###Scope
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
### Babling & capturing

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
