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

if (message) { // Because it's the same as (messsage == true), and 0 is converted to false (type coercion), so the result is false.
	console.log(message);
} else {
	console.log('No message'); // 'No message'
}
```

+ [Example](https://repl.it/CDoT)
+ [Learn more about converting values in JavaScript](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20%26%20grammar/ch4.md#converting-values)

## Duplicates

Without 'strict' mode:

```js
function logModels(model3, model2, model3) {
	console.log(model3);
}

logModels('Model S', 'Model X', 'Model ≡'); // 'Model ≡'
```

+ [Example](https://repl.it/CDox)

With 'strict' mode:

```js
function logModels(model3, model2, model3) {
	'use strict';
	console.log(model3);
}

logModels('Model S', 'Model X', 'Model ≡'); // SyntaxError: Duplicate parameter name not allowed in this context
```

+ [Example](https://repl.it/CDoy)

## Octal numbers

```js
var number1 = 020; // shortcut for creating octal number
var number2 = 100;

console.log(number1 + number2); // 116
```

+ [Example](https://repl.it/CDpA)

## Async Patters

### Callback

```js
function sendMessage(message, callMeWhenDone) {
	setTimeout(function () {
		console.log(message);
		callMeWhenDone();
	}, 1000);
}

sendMessage('Everything works.', function () {
	sendMessage('Not everything', function () {
		sendMessage('works', function () {
			sendMessage('for you.', function () {});
		});
	});
});
```

+ [Example](https://repl.it/CDqB)

```js
function sendMessage(message, callMeWhenDone) {
	setTimeout(function () {
		console.log(message);
		callMeWhenDone();
	}, 1000);
}

function sendMessage2() {
	sendMessage('Not everything', sendMessage3);
}

function sendMessage3() {
	sendMessage('works', sendMessage4);
}

function sendMessage4() {
	sendMessage('for you.', finish);
}

function finish() {}

sendMessage('Everything works.', sendMessage2);
```

+ [Example](https://repl.it/CDqE)

### Promises

```js
function sendMessage(message) {
  return new Promise(function (fulfill, reject) {
	setTimeout(function () {
		console.log(message);
		fulfill();
	}, 1000);
  });
}

function sendMessage2() {
	sendMessage('Not everything').then(sendMessage3);
}

function sendMessage3() {
	sendMessage('works').then(sendMessage4);
}

function sendMessage4() {
	sendMessage('for you.').then(finish);
}

function finish() {}

sendMessage('Everything works.').then(sendMessage2);
```

+ [Example](http://jsbin.com/wujetequzu/edit?js,console)

```js
function sendMessage(message) {
  return new Promise(function (fulfill, reject) {
	setTimeout(function () {
		console.log(message);
		fulfill();
	}, 1000);
  });
}

function sendMessage2() {
	return sendMessage('Not everything');
}

function sendMessage3() {
	return sendMessage('works');
}

function sendMessage4() {
	return sendMessage('for you.');
}

function finish() {}

sendMessage('Everything works.')
  .then(sendMessage2)
  .then(sendMessage3)
  .then(sendMessage4)
  .then(finish);
```

+ [Example](http://jsbin.com/duravipumo/edit?js,console)


