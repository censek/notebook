- [中文文档 —— 快速开始](https://vuetifyjs.com/zh-Hans/getting-started/quick-start)

##### 1. 安装
```j
npm install --save vuetify
```
##### 2. 在 `main.js` 中引入并使用
```javascript
// main.js
// 引入vuetify
import Vuetify from 'vuetify'
// 使用vuetify
Vue.use(Vuetify)
```
##### 3. 安装字体和图标
- 方法 1⃣️ ：**在 `index.html` 中引入**
```html
<link href="https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900" rel="stylesheet">
<link href="https://cdn.jsdelivr.net/npm/@mdi/font@3.x/css/materialdesignicons.min.css" rel="stylesheet">
```
- 方法 2⃣️ ：**`npm` 安装**
```j
npm install material-design-icons-iconfont -D
npm install @mdi/font -D
```
##### 4. 引入 vuetify 样式
```javascript
import 'vuetify/dist/vuetify.min.css'
```
##### 5. 开始使用
- **在 `app.vue`  中必须使用 `<v-app></v-app>` 包裹组件**。
- `Error: Vuetify is not properly initialized` 的解决方案：
在 `main.js` 中的 `new Vue({})` 里加上：**`vuetify: new Vuetify(),`**。
```javascript
// main.js
new Vue({
  //定义Vue绑定的根元素
  el: '#app',
  //将上面声明的路由器传递到根Vue实例
  router,
  //初始化Vuetify
  vuetify: new Vuetify(),
  //声明App组件，这样<App/>元素就可以生效
  components: {
    App
  },
  //用<App/>代替根元素
  template: '<App/>'
}).$mount('#app') //将这个实例挂载到id=app的根元素上
```
```html
<!-- App.vue -->
<template>
  <v-app id="app">
    <!--路由管道标签，任何符合某一路由(route)信息的组件都会在这个标签内展示出来 -->
    <router-view></router-view>
  </v-app>
</template>
```
- 然后在各 `.vue` 文件中使用 Vuetify 组件即可。
