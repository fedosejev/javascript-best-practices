# Collection of best practices in JavaScript

## Automatic Semicolon Insertion

```js
var brand = 'Tesla'
var car = brand

['Model 3'].forEach(function produce() {}); // TypeError: Cannot read property 'forEach' of undefined
```

+ [Example](https://repl.it/CDkz)


