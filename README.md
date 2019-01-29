# nerv-hyperscript [![Build Status](https://travis-ci.org/mlmorg/nerv-hyperscript.svg?branch=master)](https://travis-ci.org/mlmorg/nerv-hyperscript)

Hyperscript syntax for Nerv.js markup.

## Usage

```js
var h = require('nerv-hyperscript');
var Nerv = require('nerv');

var AnotherComponent = require('./another-component');

module.exports = Nerv.createClass({
  render: function render() {
    return (
      h('div.example', [
        h('h1#heading', 'This is hyperscript'),
        h('h2', 'creating Nerv.js markup'),
        h(AnotherComponent, {foo: 'bar'}, [
          h('li', [
            h('a', {href: 'http://whatever.com'}, 'One list item')
          ]),
          h('li', 'Another list item')
        ])
      ])
    );
  }
});
```

## Documentation

**Object.assign is used in this library and is *not* poly-filled.**

#### `h(componentOrTag, properties, children)`

Returns a Nerv element.

- **componentOrTag** `Object|String` - Can be a Nerv component **OR** tag
string with optional css class names/id in the format `h1#some-id.foo.bar`.
If a tag string, it will parse out the tag name and change the `id` and
`className` properties of the `properties` object.
- **properties** `Object` *(optional)* - An object containing the properties
you'd like to set on the element.
- **children** `Array|String` *(optional)* - An array of `h()` children or
a string. This will create child elements or a text node, respectively.
- **listOfElements** `Array` - An array of Nerv elements that will be wrapped with `Nerv.Fragment`.
