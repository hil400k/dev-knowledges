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
    Web server sends certificate (with public key) to the browser -> 
    Browser sends certificate verified message to server
Browser generates symmetric key and encrypts it using public key (key from the server) ->
Browser sends this encrypted symmetric key to the server -> 
This encrypted key is used for entire session.
```

> Symmetric key means that we need the same key to encrypt and decrypt. Asymmetric is opposite.
