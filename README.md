# Collection of best practices in JavaScript

## Automatic Semicolon Insertion

```js
var brand = 'Tesla'
var car = brand

['Model 3'].forEach(function produce() {}) // TypeError: Cannot read property 'forEach' of undefined
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

console.log(getMessage()) // 'undefined'
```

+ [Example](https://repl.it/CDlI)

## Equaity

```js
var message = 0;

if (message) { // Because it's the same as (messsage == true), and 0 is converted to false (type coercion), so the result is false
	console.log(message);
} else {
	console.log('No message'); // 'No message'
}
```

+ [Example](https://repl.it/CDoT)
+ [Learn more about converting values in JavaScript](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20%26%20grammar/ch4.md#converting-values)

