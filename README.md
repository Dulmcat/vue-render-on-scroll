# vue-render-on-scroll
`vue-render-on-scroll` -  A Vue component that allows you to lazy-load components as they appear on screen. Great for passing google speed tests. It basicly adds `v-if="false"` to the content of the component as long as it did not yet apear on your screan.

## install
```sh 
npm i vue-render-on-scroll
```
or
```sh 
yarn add vue-render-on-scroll
```

## Usage
```html
<vue-render-on-scroll>
  <div>This content will be loaded only when it enters viewport</div>
</vue-render-on-scroll>
```
js global
```js
import vue-render-on-scroll from 'vue-render-on-scroll`,
Vue.component('vue-render-on-scroll', vue-render-on-scroll)
```
js local
```js
import vue-render-on-scroll from 'vue-render-on-scroll`,
...
export default {
    components: {
      vue-render-on-scroll
    },
}
```