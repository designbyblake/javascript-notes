# From IIFEs to CommonJS to ES6 Modules

## Module
- Reusability
- Composability
- Leverage
- Isolation
- Organization

Each module has three parts - dependencies (also called imports), code, and exports.

## Immediately Invoked Function Expression
Protects code from being globablly scoped
```JS
(function () {
  console.log('Pronounced IF-EE')
})()
```