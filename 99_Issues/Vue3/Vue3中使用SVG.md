# 基本实现（2022-04-02）



## 一、创建SVG组件库

- ##### 创建SvgIcon文件夹

- ##### 在SvgIcon文件夹下创建文件 svg存放.svg文件

- ##### 在SvgIcon文件夹下创建文件index.js

  ```js
  // index.js 目的是将所有.svg文件按照模块引入
  const requireAll = (requireContext) => requireContext.keys().map(requireContext)
  const req = require.context('./svg', false, /\.svg$/)
  requireAll(req)
  
  ```

- ##### 在SvgIcon文件夹下创建文件index.vue

  ```vue
  // index.vue svg组件
  <template>
    <div>
      <svg :class="svgClass" aria-hidden="true">
        <use :xlink:href="iconName" />
      </svg>
    </div>
  </template>
  <script setup>
  import { defineProps, computed } from 'vue'
  // name: 'svgIcon',
  const props = defineProps({
    iconClass: {
      type: String,
      required: true
    },
    className: {
      type: String,
      default: ''
    }
  })
  const iconName = computed(() => {
    return `#icon-${props.iconClass}`
  })
  const svgClass = computed(() => {
    if (props.className) {
      return 'svg-icon' + props.className
    } else {
      return 'svg-icon'
    }
  })
  </script>
  <style scoped>
  .svg-icon {
    padding-right: 1em;
    width: 1em;
    height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }
  </style>
  
  
  ```

  

## 二、对SVG组件库进行注册



```js
// 编写注册组件的方法(scr下新建global文件夹，在global文件下新建index.js和register-svg.js)
// index.js作为global文件夹的统一出口
import '@/components/svgIcon/index.js'
import SvgIcon from '@/components/svgIcon/index.vue'
const registerSvg = function (app) {
  app.component('svg-icon', SvgIcon)
}
export default registerSvg

// 在mian.js中导入注册函数
import { createApp } from 'vue'
import App fromn './App.vue'
import registerSvg from '@/global'
const app = createApp(App)
registerSvg(app) // 注册
```



## 三、配置loader（重点）

- ##### 安装loader：npm install svg-sprite-loader -D

- ##### 配置vue.config.js

  ```js
  // "svg-sprite-loader": "^6.0.11"
  const path = require('path')
  function resolve(dir) {
    return path.join(__dirname, '.', dir)
  }
  
  
  module.export = {
    chainWebpack: (config) => {
      config.module.rules.delete('svg') //重点:删除默认配置中处理svg,
      config.module
        .rule('svg-sprite-loader')
        .test(/\.svg$/)
        .include.add(resolve('src/components/svgIcon/svg')) //处理svg目录
        .end()
        .use('svg-sprite-loader')
        .loader('svg-sprite-loader')
        .options({
          symbolId: 'icon-[name]'
        })
    }
  }
  ```
  
  

## 四、页面中使用

```vue
// svg组件名: name.svg 中的name
<svg-icon :icon-class="svg组件名" />
```

