

# 基本实现(2022-4-18)



## 一、安装element-plus：

```shell
npm install element-plus --save
```



## 二、安装自动导入插件unplugin-vue-components` 和 `unplugin-auto-import：

```shell
npm install -D unplugin-vue-components unplugin-auto-import
```



## 三、webpack配置

```shell
// vue.config.js
const AutoImport = require('unplugin-auto-import/webpack')
const Components = require('unplugin-vue-components/webpack')
const { ElementPlusResolver } = require('unplugin-vue-components/resolvers')

module.export = {
// ....
	configureWebpack: {
		plugins: [
      AutoImport({
        imports: ['vue'],
        resolvers: [
          ElementPlusResolver({
            importStyle: 'css',
            exclude: new RegExp(/^(?!.*loading-directive).*$/)
          })
        ]
      }),
      Components({
        resolvers: [
          ElementPlusResolver({
            importStyle: 'css'
          })
        ]
      })
    ]
	}
}


// 对于某些以service方式调用的需要单独导入样式，例如：
import { ElMessage, ElMessageBox } from 'element-plus'
import 'element-plus/es/components/message-box/style/css'
import 'element-plus/es/components/message/style/css'
```



## 四、编写全局注册组件的方法：

```js
import { ... } from 'element-plus'
const components = [...]
function registerElement(app) {
  for (const component of components) {
    app.component(component.name, component)
  }
}
export default registerElement
```

