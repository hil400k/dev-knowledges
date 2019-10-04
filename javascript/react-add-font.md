### React-create-app add font
- download fonts (example: Marienkaefer - TTF.ttf)
- create src/fonts & paste fonts inside it
- index.css: 
```css
@font-face {
  font-family: 'Marienkaefer';
  src: local('Marienkaefer'), url('fonts/Marienkaefer - TTF.ttf') format('truetype');
}
body {
    font-family: Marienkaefer;
}
```
- index.js: 
```js
import './fonts/Marienkaefer - TTF.ttf';
```