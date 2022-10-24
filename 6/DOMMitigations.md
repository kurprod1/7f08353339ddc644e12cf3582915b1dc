# Mitigations

Created: June 22, 2022 1:17 PM

DOM-based vulnerability berasal dari celah script yang tidak terstruktur atau tidak adanya validator pada input.

Berikut beberapa sink atau celah script yang dapat memicu DOM-based XSS antara lain:

```
document.write()
document.writeln()
document.domain
element.innerHTML
element.outerHTML
element.insertAdjacentHTML
element.onevent
```

Dan berikut sink dari JQuery

```
add()
after()
append()
animate()
insertAfter()
insertBefore()
before()
html()
prepend()
replaceAll()
replaceWith()
wrap()
wrapInner()
wrapAll()
has()
constructor()
init()
index()
jQuery.parseHTML()
$.parseHTML()
```