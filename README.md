# hscrpt

`hscrpt` is a sugar-free version of [hyperscript](https://github.com/dominictarr/hyperscript')

sometimes you need to create a very basic UI,
but also want an absolutely minimal code size.

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








