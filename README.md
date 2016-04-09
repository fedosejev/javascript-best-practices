# Collection of best practices in JavaScript

## Automatic Semicolon Insertion

```js
var brand = 'Tesla'
var car = brand

['Model 3'].forEach(function produce() {}); // TypeError: Cannot read property 'forEach' of undefined
```

+ [Example](https://repl.it/CDkz)

```js
var brand = 'Tesla'
var car = brand

(function produce() {})() // TypeError: brand is not a function
```

+ [Example](https://repl.it/CDlC)

```js
function getMessage() {
	return
	{
		message: 'Oops!'
	}
}

console.log(getMessage());
```

+ [Example](https://repl.it/CDlI)
