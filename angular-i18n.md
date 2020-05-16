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
`<span i18n>The author is {gender, select, male {male} female {female} other {other}}</span>`
