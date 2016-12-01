# babel-plugin-transform-do-expressions

> Compile do expressions to ES5

## Example

### In JSX
One of the most useful usage of the `do` expression is inside JSX. If we want to conditionally display a component we usually have to call another function which would implement the condition and return the correct value, for example:

```js
const getColoredComponent = color => {
  if(color === 'blue') { return <BlueComponent/>; }
  if(color === 'red') { return <RedComponent/>; }
  if(color === 'green') { return <GreenComponent/>; }
}

const Component = props =>
  <div className='myComponent'>
    {getColoredComponent()}
  </div>
;
```

Using a do expression you can add logic inside JSX:

```js
const Component = props =>
  <div className='myComponent'>
    {do {
      if(color === 'blue') { <BlueComponent/>; }
      if(color === 'red') { <RedComponent/>; }
      if(color === 'green') { <GreenComponent/>; }
    }}
  </div>
;
```

[Try in REPL](/repl/#?evaluate=true&presets=es2015%2Creact%2Cstage-0&code=const%20Component%20%3D%20props%20%3D%3E%0A%20%20%3Cdiv%20className%3D'myComponent'%3E%0A%20%20%20%20%7Bdo%20%7B%0A%20%20%20%20%20%20if(color%20%3D%3D%3D%20'blue')%20%7B%20%3CBlueComponent%2F%3E%3B%20%7D%0A%20%20%20%20%20%20if(color%20%3D%3D%3D%20'red')%20%7B%20%3CRedComponent%2F%3E%3B%20%7D%0A%20%20%20%20%20%20if(color%20%3D%3D%3D%20'green')%20%7B%20%3CGreenComponent%2F%3E%3B%20%7D%0A%20%20%20%20%7D%7D%0A%20%20%3C%2Fdiv%3E%0A%3B)

## Installation

```sh
npm install --save-dev babel-plugin-transform-do-expressions
```

## Usage

### Via `.babelrc` (Recommended)

**.babelrc**

```json
{
  "plugins": ["transform-do-expressions"]
}
```

### Via CLI

```sh
babel --plugins transform-do-expressions script.js
```

### Via Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-do-expressions"]
});
```

## References
- [Proposal](http://wiki.ecmascript.org/doku.php?id=strawman:do_expressions)
- [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS/blob/master/types%20%26%20grammar/ch5.md#statement-completion-values)
- Very handy for conditions inside JSX: [reactjs/react-future#35](https://github.com/reactjs/react-future/issues/35#issuecomment-120009203)
