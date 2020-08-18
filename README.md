# vue-page-designer

<p align="center">
  <a href="https://fireyy.github.io/vue-page-designer/" target="_blank">
    <img src="screen.png" width="700px">
    <br>
    Live Demo
  </a>
</p>

A drag-and-drop mobile website builder base on Vue.

## Install

```bash
yarn add vue-page-designer
```

You can start it quickly, in main.js:

```js
import Vue from 'vue';
import vuePageDesigner from 'vue-page-designer'
import 'vue-page-designer/dist/vue-page-designer.css'
import App from './App.vue';

Vue.use(vuePageDesigner);

new Vue({
  el: '#app',
  render: h => h(App)
});
```

Next, use it:

```html
<template>
  <div id="app">
    <vue-page-designer />
  </div>
</template>

<style>
#app {
  height: 100%;
}
</style>
```

A [example](https://fireyy.github.io/vue-page-designer/) ▶️, and [source](./example/). Also a [custom widget source](./example/widgets)

# Options

You can add custom components, save callback.

| Props | Type | Description |
| -------- | -------- | -------- |
| value | `Object` | Editor initial value, you can pass the value of the save callback and resume the draft |
| locale | `String` | Editor default locale. Now support 'cn' and 'en', default 'cn'. |
| widgets | `Object` | Vue Components. Custom components for editor. see [Example](https://github.com/fireyy/vue-page-designer-widgets/blob/master/src/index.js) |
| save | `(data) => void` | When you click the Save button, feed back to you to save the data |
| upload | `(files) => Promise` | Editor upload function, allowing you to implement your own upload-file's request |

## Parameter: `value`

The `value` came from `save`.

```html
<template>
  <div id="app">
    <vue-page-designer :value="value" />
  </div>
</template>
```

## Parameter: `widgets`

You can install default widget in `vue-page-designer-widgets`

```bash
yarn add vue-page-designer-widgets
```

Import and use it

```html
<template>
  <div id="app">
    <vue-page-designer :widgets="widgets" />
  </div>
</template>
<script>
import widgets from './widgets'

export default {
  data () {
    return {
      widgets
    }
  }
}
</script>
```

Set locale to EN

```html
<template>
  <div id="app">
    <vue-page-designer locale="en" />
  </div>
</template>
```

## Parameter: `save`

```html
<template>
  <div id="app">
    <vue-page-designer @save="(data) => { console.log('send the value data to your server', data) }" />
  </div>
</template>
```

## Parameter: `upload`

```html
<template>
  <div id="app">
    <vue-page-designer :upload="upload" />
  </div>
</template>
<script>
export default {
  methods: {
    upload (files) {
      return yourApiUpload(files).then(res => {
        return res.data
      }).catch(err => {
        console.log(err)
      })
    }
  }
}
</script>
```
