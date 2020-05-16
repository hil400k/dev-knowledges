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
