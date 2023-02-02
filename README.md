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
> with some convenience wrappers over the APIs provided by the two libraries.

<br>
