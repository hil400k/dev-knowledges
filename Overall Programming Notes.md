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
