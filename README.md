<div align="center">
  <img src="./logo-light.svg#gh-light-mode-only" height="72px" />
  <img src="./logo-dark.svg#gh-dark-mode-only" height="72px" />
  <br><sup>SSR for Web Components</sup>
</div>

<br>

```js
// my-component.js
import { definition } from 'hydron'

class MyComponent extends HTMLElement {
  // ...
}

export default definition('my-component', MyComponent)
```
```js
// index.js
import { Page } from 'hydron'
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
