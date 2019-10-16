## What is the difference between `var`, `const` and `let` ?
### `let`, `const`:
  - block level scope,
  - initialize during variable definition (no hoisting),
  - global functions and variables declared with `const` or `let` **does not** become property of the global object.
### `var`:
  - has no block level scope,
  - variables declared with `var` and `function` are initialized just before script is run (initialization phase) and have assigned `undefined` value (hoisting - rising),
  - `var` declaration are processed at the function start (hoisted - rised),
  - declarations are hoisted but assignments are not,
  - global functions and variables declared with `var` become property of the global object.

```javascript
const something = 'nothing';
```

