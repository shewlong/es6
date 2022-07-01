#### 在webpack中使用cdn加速优化,减少打包体积，减少用户访问时间



------

[TOC]



##### 1.引入cdn资源

​    <!-- built files will be auto injected -->
​    

```html
<link rel="stylesheet" href="https://unpkg.com/element-ui@2.3.5/lib/theme-chalk/index.css" />
<link rel="stylesheet" href="https://unpkg.com/vant@1.1.2/lib/vant-css/index.css" />
```

 <script src="https://cdn.bootcss.com/vue/2.5.2/vue.min.js"></script>
 <script src="https://cdn.jsdelivr.net/npm/vue-router@3.0.1/dist/vue-router.min.js"></script>
 <script src="https://cdn.jsdelivr.net/npm/vuex@3.0.1/dist/vuex.min.js"></script>
 <script src="https://unpkg.com/element-ui@2.3.5/lib/index.js"></script>
 <script src="https://cdn.jsdelivr.net/npm/vant@1.1.2/lib/vant.min.js"></script>
 <script src="https://cdn.staticfile.org/axios/0.17.1/axios.min.js"></script>

​    <!-- built files will be auto injected -->

注：1.该文件为项目入口html文件，通常处于项目public目录下或者项目根目录下，使用了vant和elementUi,2.所以还应该引入相对应得css资源包3.cdn加速地址可以在官网中找到

代码展示

![image-20220630154543458](https://github.com/shewlong/shewlong.github.io/blob/main/screenshots/image-20220630154543458.png?raw=true)

##### 2.在webpack基础配置文件中加入externals配置，打包、编译时去除cdn加速的模块，可以大大压缩打包后的压缩包体积

```javascript
  externals: {

   vue: 'Vue',

   'vue-router': 'VueRouter',

   "element-ui": "ElementUI",

   'vant':"Vant",

   axios: 'axios',

   vuex: 'Vuex',

  },
```

代码展示

![image-20220630155356136](https://github.com/shewlong/shewlong.github.io/blob/main/screenshots/image-20220630155356136.png?raw=true)

##### 3.去除main.js中对以上模块的引用，注册

![image-20220630155523759](https://github.com/shewlong/shewlong.github.io/blob/main/screenshots/image-20220630155523759.png?raw=true)