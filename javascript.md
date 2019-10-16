# What is the difference between `var`, `const` and `let` ?
## `let`, `const`:
  1. block level scope,

```javascript
function checkTheCondition() {
  if (true) {
    let test = true;
  }

  console.log(test); // Error: test is not defined
}
```

  2. initialize during variable definition (no hoisting),

```javascript
function sayMaybe() {
  phrase = "I'm not sure";

  console.log(phrase); // Error: Cannot access 'phrase' before initialization

  let phrase;
}
```

  3. global functions and variables declared with `const` or `let` **does not** become property of the global object.

```javascript
const globalVariable = 5;

console.log(window.globalVariable); // undefined (doesn't become a property of the global object)
```


## `var`:
  1. has no block level scope - ignores code blocks,

```javascript
function doTheLoop() {
  for (var i = 0; i < 10; i =+1) {}

  console.log(i); // 10
}
```

  2. has functional or global scope,

```javascript
function functionalScope() {
  var x = 10;
  console.log(x); // 10

  if (true) {
    var x = 20;
    console.log(x); // 20
  }

  console.log(x); // 20
}

console.log(x) // Error: x is not defined
```

  3. `var` and `function` declarations are processed at the function start or script starts for globals (hoisted - rised) and have assigned `undefined` value,

```javascript
function sayHi() {
  console.log('before assignment:', phrase); // undefined

  phrase = 'Hello';

  console.log('after assignment:', phrase); // Hello

  var phrase;
}

function sayBye() {
  phrase = 'Goodbye';

  if (false) {
    var phrase;
  }

  console.log(phrase); // Goodbye
}
```

  4. declarations are hoisted but assignments are not, they work at the place where they appear,

```javascript
function sayWhy() {
  var phrase; // declaration works at the start

  console.log(phrase); // undefined

  phrase = 'Because I want to'; // assignment when the execution reaches it
}
```

  5. global functions and variables declared with `var` **become** property of the global object.

```javascript
var globalVariable = 5;

console.log(window.globalVariable); // 5 (became a property of the global object)
```


