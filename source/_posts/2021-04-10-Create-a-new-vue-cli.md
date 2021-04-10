---
title: Create a new vue cli
comment: true
date: 2021-04-10 10:42:22
categories: [vue]
tags:
---
# 安裝 Vue Cli

課程是以 vue-cli 2 的版本，如果是這個版本，可以執行以下：

```bash
$ vue init webpack <project name>
```

<!--more-->
如果你跟我一樣裝了 vue cli3 ，可以使用 vue create <專案名>，安裝時可選擇 vue 2 版本

```bash
$ vue create <project name>

// 執行
npm run serve
```

註：`npm run dev` 跟 `npm run serve` 只是在 package.json 裡的名稱不同而已

# 安裝 Bootstrap node-sass sass-loader

```bash
$ npm install bootstrap node-sass sass-loader --save
```

測試 scss 有沒有裝好


```jsx app.vue
<style lang="scss">
  $color: black;

  body {
    background-color: $color;
  }
</style>
```

style裡改用 @import 方式引入 BS，放入 BS HTML 元件看效果

```jsx
<template>
  <div id="app">

<!-- 要顯示的內容一定要放在 #app 裡面 -->

    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
    
    <div class="card" style="width: 18rem;">
      <div class="card-body">
        <h5 class="card-title">Card title</h5>
        <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's
          content.</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
    
<!-- 要顯示的內容一定要放在 #app 裡面 -->

  </div>

</template>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
</style>
```

在 HelloWorld.vue 上有 scoped 限制樣式只能在該元件上

```jsx
<style scoped lang="scss">
```

# install axios

url: [https://www.npmjs.com/package/vue-axios](https://www.npmjs.com/package/vue-axios)

```bash
$ npm install --save axios vue-axios
```

at main.js import


```jsx main.js
import axios from 'axios'
import VueAxios from 'vue-axios'
// use
Vue.use(VueAxios, axios)
```

如果你不小心安裝了 es-lint ，運行時出現提示應修正錯誤，可以用以下指令查找主要錯誤的地方。

顯示主要錯誤（忽略prettier）

```jsx
npm run lint --fix

> vue-shop@0.1.0 lint
> vue-cli-service lint

error: 'HelloWorld' is defined but never used (no-unused-vars) at src/App.vue:29:8:
  27 |
  28 | <script>
> 29 | import HelloWorld from "./components/HelloWorld";
     |        ^
  30 |
  31 | export default {
  32 |   name: "App",

1 error found.
```

如果修正錯誤後沒有問題，則會出現…

```jsx
npm run lint --fix

> vue-shop@0.1.0 lint
> vue-cli-service lint

 DONE  No lint errors found!
```

使用 axios

```jsx
<script>
export default {
  name: "App",
  created() {    // 我不小心打成 create() 測試半天才找到原因
    this.$http.get("https://randomuser.me/api/").then((response) => {
      console.log(response);
    });
  },
};
</script>
```

# 增加自訂 API 路徑

就是我們申請的自訂 API 路徑。課程說要修改 config\ 目錄下的設定檔，增加 API 常數，但使用新版本 Vue Cli3 在根目錄中已經沒有 config 、build 等目錄，如果要加常數，要在「根目錄」加入「.env」檔案，內容為：

```jsx
常數名稱=value
```

常數一定要以 VUE_APP_ 為前置命名，例如：

```jsx
VUE_APP_{variable name}=value

example:
VUE_APP_APIPATH=https://vue-course-api.herokuapp.com
VUE_APP_CUSTOMPATH=joe
```

改完要重新運行服務才會生效。據網上資料，如果輸出常數得到 undefined ，可能原因有三種：

1. .env 沒在根目錄，如在 /src

2. 要以 VUE_APP_ 開頭，如果沒有，也會出現 undefined

3. 改完要重啟服務 npm run serve

# 組合 api 路徑，測試是否正常


```jsx app.vue
<script>
export default {
  created(){
    const api = `${process.env.VUE_APP_APIPATH}/api/${process.env.VUE_APP_CUSTOMPATH}/products`

    this.$http.get(api)
      .then((response) =>{
        console.log(response)
      })
  }
}
</script>
```

得到結果：
![alt](01.png)

# 🌍  Resources

|D2| Vue CLI3 安裝與建立 vue 專案 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天
[https://ithelp.ithome.com.tw/articles/10216606](https://ithelp.ithome.com.tw/articles/10216606)

解讀 vue-cli 腳手架（一）：npm run dev的背後 - IT閱讀
[https://www.itread01.com/content/1550372949.html](https://www.itread01.com/content/1550372949.html)