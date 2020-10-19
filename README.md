# vue-sticky-directive

This is a fork of `vue-sticky-directive` for Vue 3.

# Install

```bash
$ yarn add vue-sticky-directive
```

ES2015
```js
// register globally
import Sticky from 'vue-sticky-directive'

createApp(App).use(Sticky)

// or for a single instance
import { Sticky } from 'vue-sticky-directive'

export default defineComponent({
  directives: {
    Sticky
  }
})
```

# Usage

Use `v-sticky` directive to enable element position sticky. Sticky element will find its nearest element with `sticky-container` attribute or its parent node if failed as the relative element.

[basic example](https://mehwww.github.io/vue-sticky-directive/examples/basic/)

```html
<div sticky-container>
  <div v-sticky="{ offset, side: 'top' }">
    ...
  </div>
</div>
```

# Options
* `offset` - set sticky offset, it support a vm variable name or a js expression like `{top: 10, bottom: 20}`
  * `top`_(number)_ - set the top breakpoint (default: `0`)
  * `bottom`_(number)_ - set the bottom breakpoint (default: `0`)
* `side`_(string)_ - decide which side should be sticky, you can set `top`、`bottom` or `both` (default: `top`)
* `zIndex` _(number)_ - to set the z-index of element to stick
* `onStick` _(function)_ - callback when sticky and release, receiveing 1 argument with object indicating the state, like:

```js
// The element is stuck on top
{
  bottom: false,
  top: true,
  stuck: true
}
```

```html
<div sticky-container>
  <div v-sticky="options">
    ...
  </div>
</div>
```

```js
export default {
  data () {
    return {
      enabled: true,
      offset: {
        top: 0,
        bottom: 0
      },
      side: 'top',
      zIndex: 10,
      onStick({ top, bottom, stuck }) {
        // do stuff
      }
    }
  }
}
```

# License

MIT


