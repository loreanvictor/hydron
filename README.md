<div align="center">
  <img src="./logo-light.svg#gh-light-mode-only" height="72px" />
  <img src="./logo-dark.svg#gh-dark-mode-only" height="72px" />
  <br><sup>SSR for Web Components</sup>
</div>

<br>

```js
// my-component.js
import { packMe } from 'hydron'

class MyComponent extends HTMLElement {
  // ...
}

export default registry => {
  packMe()
  registry.define('my-component', MyComponent)
}
```
```js
// index.js
import { Page } from 'hydron'
import myComp from './my-component'

const page = new Page()
page.use(myComp)

page.document.body.innerHTML = '<my-component></my-component>'
page.write('dist/index.html')
```

<br>
