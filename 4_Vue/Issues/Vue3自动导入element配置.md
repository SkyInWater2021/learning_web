

# 基本实现(2022-4-18)



## 1、安装element-plus：

```shell
npm install element-plus --save
```



## 2、安装自动导入插件`unplugin-vue-components` 和 `unplugin-auto-import`：

```shell
npm install -D unplugin-vue-components unplugin-auto-import
```



## 3、webpack配置

```js
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



## 4、编写全局注册组件的方法：

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

