### Features: 
- displaying date, numbers, percentages and currencies on local format
- preparing template captions for translations
- handling plural forms of verbs

To add i18n to angular project: `ng add @angular/localize`

To add Locale specific utils you neex to import them explicitly. For example:
```
import { registerLocaleData } from '@angular/common';
import localeFr from '@angular/common/locales/fr';
import localeFrExtra from '@angular/common/locales/extra/fr';

registerLocaleData(localeFr, 'fr-FR', localeFrExtra);
```

To add a caption to translation file you should add `i18n` attr

btw, you can specify description for this caption `i18n="Text for header"` and meaning + description
`i18n="header-text|Text for header"`
Meaning allows to extract only one translation item and translation will be used in all places with this meaning

To set custom id `<h1 i18n="@@introductionHeader">Hello i18n!</h1>`

To mark attribute for translation use `i18n-attr`, e.g. `title` will be `i18n-title`. And you can specify meaning, desc, custom id.

If you need a translation depended on variable value you need to translate all of alternative messages.
E.g. Gender is a component prop. Select is i18n operator. male, female, other are possible values.
```
<span i18n>The author is {gender, select, male {male} female {female} other {other}}</span>
```

To create source file: `ng xi18n --output-path src/locale --out-file source.xlf `

To set base locale: `ng xi18n --i18n-locale fr`

To translate source text you need to use `terget` element
```
<trans-unit id="introductionHeader" datatype="html">
  <source>Hello i18n!</source>
  <target>Bonjour i18n !</target>
  <note priority="1" from="description">An introduction header for this sample</note>
  <note priority="1" from="meaning">User welcome</note>
</trans-unit>
```
`id` attr depends upon the content of the template text and its assigned meaning.

Translation of text with `select` operator consists of few parts. E.g. our <strong>gender</strong> sample
```
</trans-unit>
<trans-unit id="f99f34ac9bd4606345071bd813858dec29f3b7d1" datatype="html">
  <source>The author is <x id="ICU" equiv-text="{gender, select, male {...} female {...} other {...}}"/></source>
  <target>L'auteur est <x id="ICU" equiv-text="{gender, select, male {...} female {...} other {...}}"/></target>
</trans-unit>
<trans-unit id="eff74b75ab7364b6fa888f1cbfae901aaaf02295" datatype="html">
  <source>{VAR_SELECT, select, male {male} female {female} other {other} }</source>
  <target>{VAR_SELECT, select, male {un homme} female {une femme} other {autre} }</target>
</trans-unit>
```

### How to use translations

Open angular.json file and add next:

```
"projects": {
  ...
  "project-name": {
    ...
    "i18n": {
      "sourceLocale": "en-US",
      "locales": {
        "ua": "src/locale/messages.ua.xlf"
      }
    }
  }
}
```
Here you specify sourceLocale and paths to locales

To build packages for all languages `ng build --localize`, for specific `ng build --localize=ua`

To apply specific build options to only one locale, you can create a custom locale-specific configuration. In this case, the localize option specifies the single locale, as shown here.
```
"build": {
  ...
  "configurations": {
    ...
    "fr": {
      "localize": ["fr"],
      "main": "src/main.fr.ts",
      ...
    }
  }
},
"serve": {
  ...
  "configurations": {
    ...
    "fr": {
      "browserTarget": "*project-name*:build:fr"
    }
  }
}
```
You can run with: `ng serve --configuration=fr`

> Development server supports only one locale per build !!!
> Angular i18n doesn't support dynamic languages

