<div align="center">
  <img src="./logo-light.svg#gh-light-mode-only" height="72px" />
  <img src="./logo-dark.svg#gh-dark-mode-only" height="72px" />
  <br><sup>SSR for Web Components</sup>
</div>

<br>

```js
// my-component.js
import { mod } from 'hydron'

//
// hydron actually doesn't care about components, except
// for using a serializer that properly supports declarative shadow dom.
// instead it works with "modifications" to given `window` objects.
//
export default mod(window => {
  class MyComponent extends window.HTMLElement {
    // ...
  }

  window.customElements.define('my-component', MyComponent)
})
```
```js
// index.js
import { Page } from 'hydron/server'
import myComp from './my-component'

const page = new Page()
page.use(myComp)

page.document.body.innerHTML = '<my-component></my-component>'
page.save('dist/index.html')
```

<br>

> _WORK IN PROGRESS_
>
> My current idea of implementing this is [packen](https://github.com/loreanvictor/packen) + [Happy DOM](https://github.com/capricorn86/happy-dom)
> with some convenience wrappers over the APIs provided by the two libraries. This means the solution will be dependent on [declarative shadow DOM](https://web.dev/declarative-shadow-dom/)
> which is yet to be supported by all major browsers ([currently its Chrome and Edge](https://caniuse.com/declarative-shadow-dom)). There are
> possible work-arounds for this limitation, for example forgoing encapsulation and inlining components that can be inlined, but I feel those will fall
> out of the scope of this project, although it should play nice with them.

<br>

Some usage examples:

```js
// server-only modifications
import { mod } from 'hydron/server'

export default mod(window => ...)
```
```js
// dependency between mods (e.g. components needing each other)
import { mod, use } from 'hydron'
import OtherMod from './other-mod'

export default mod(window => {
  use(OtherMod)
  // ...
})
```


<br>
