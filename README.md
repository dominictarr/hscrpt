# hscrpt

`hscrpt` is a sugar-free version of [hyperscript](https://github.com/dominictarr/hyperscript)

It's not a framework, it's just a tool for convienently creating html
elements directly in javascript.

``` js
//reactive hello world
var h = require('hscrpt')
var name
document.body.appendChild(h('div', [
  h('h1', [ 'Hello, ', name = h('span', 'World') ]),
  h('input', {oninput: function (ev) {
    name.textContent = ev.target.value
  }})
]))
```

frameworks come and go. but the DOM doesn't change,
because that would _break all the frameworks_.

You could do this with `hyperscript`, this just removes all the sugar
from hyperscript and gives you something absolutely minimal.

infact:
``` js
module.exports = function h (tag, attrs, content) {
  if(Array.isArray(attrs)) content = attrs, attrs = {}
  var el = document.createElement(tag)
  for(var k in attrs) el[k] = attrs[k]
  if(content) content.forEach(function (e) {
    if(e) el.appendChild('string' == typeof e ? document.createTextNode(e) : e)
  })
  return el
}
```
^ you just read the entire codebase of `hscrpt`.

# api: h(tagname, attrs?, children?)

only `tagname` is mandatory. it must be a string.
if given, `attrs` must be an `{}`
and children must be an [].

## setting classes

use `h('div', {classList: 'content'})`
(same as `h('div.content')` in 'hyperscript'.)

## setting event listeners

use `h('button', {onclick: function (ev) {...}}, ['submit'])`

## License

MIT












