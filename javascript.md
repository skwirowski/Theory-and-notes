# What is the difference between `var`, `const` and `let` ?
## `let`, `const`:
###  1. block level scope,

```javascript
function checkTheCondition() {
  if (true) {
    let test = true;
  }

  console.log(test); // Error: test is not defined
}
```

###  2. initialize during variable definition (no hoisting),

```javascript
function sayMaybe() {
  phrase = "I'm not sure";

  console.log(phrase); // Error: Cannot access 'phrase' before initialization

  let phrase;
}
```

###  3. global functions and variables declared with `const` or `let` **does not** become property of the global object,

```javascript
const globalVariable = 5;

console.log(window.globalVariable); // undefined (doesn't become a property of the global object)
```

### 4. variable declarations **can't** be re-declared.

```javascript
  let foo;
  // ...many lines later...
  let foo; // Error: Identifier 'foo' has already been declared
```


## `var`:
###  1. has no block level scope - ignores code blocks,

```javascript
function doTheLoop() {
  for (var i = 0; i < 10; i =+1) {}

  console.log(i); // 10
}
```

###  2. has functional or global scope,

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

###  3. `var` and `function` declarations are processed at the function start or script starts for globals (hoisted - rised) and have assigned `undefined` value,

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

###  4. declarations are hoisted but assignments are not, they work at the place where they appear,

```javascript
function sayWhy() {
  var phrase; // declaration works at the start

  console.log(phrase); // undefined

  phrase = 'Because I want to'; // assignment when the execution reaches it
}
```

###  5. global functions and variables declared with `var` **become** property of the global object,

```javascript
var globalVariable = 5;

console.log(window.globalVariable); // 5 (became a property of the global object)
```

### 6. variable declarations **can** be re-declared.

```javascript
  var bar;
  // ...many lines later...
  var bar; // second var is simply ignored
```

# JavaScript ECMAScript 2015 (ES6) new features.

## 1. Constants `const`
Support for constants (immutable variables), that is, variables which cannot be re-assigned new content and can't be re-declared.  
*NOTICE:*  
This only makes the variable itself immutable, not its assigned content. For instance, in case the content is an object, this means the object itself can still be altered.

## 2. Scoping
### 2.1 Block-scoped variables
Block-scoped variables `let` and `const` without hoisting.

### 2.2 Block-scoped functions
Block-scoped function definitions  
*NOTICE:*  
Bear in mind that this doesn't work without the outer blocks (encapsulating outer braces).

```javascript
{
  function foo () { return 'Hello from the first function'; }

  console.log(foo());
  {
      function foo () { return 'Hello from the second function'; }

      console.log(foo());
  }
  console.log(foo());
}
```

## 3. Arrow functions
### 3.1 Expression Bodies
More expressive closure syntax. Expressions are units of code that can be evaluated and resolve to a value.

```javascript
elements = array.map(element => element + 2);
```

##3.2 Statement Bodies
More expressive closure syntax. Statements are programming instructions to be executed by a computer.

```javascript
nums.forEach(num => {
  if (num % 5 === 0) {
    fives.push(num);
  }
})
```

### 3.3 Lexical `this`
With arrow functions the `this` keyword always represents the object that defined the arrow function. The `this` keyword represents the object that owns the function, no matter who calls the function.

## 4. Extended parameters handling