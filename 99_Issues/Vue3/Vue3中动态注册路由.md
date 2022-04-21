# 基本思路（2022-04-02）



## 一、本地编写好映射关系

- ##### router文件夹下编写好所有的路由对象

- ##### views文件夹下编写好所有的页面组件

- ##### router对象中component与views中的页面组件对应

```js
const cpnName = () => import('@/views/userMenus/XXX/XXX.vue')

export default {
  path: '/XXX/XXX',
  name: 'name',
  meta: {
    title: 'title'
  },
  component: cpnName,
  children: [],
  ...
}
```



## 二、编写匹配路由方法

```js
// 在utils中实现一个动态注册路由的方法
let firstMenu = null // 保存第一个匹配到的路由对象，路由跳转时默认跳到对应页面

export function mapMenusToRoutes(userMenus) {
  const routes = [] // 要返回的routes
  // 1. 默认获取所有本地路由对象
  const allRoutes = []
  // 1.1获取文件路径
  const routeFiles = require.context('文件路径：从哪开始找', Boolean:是否查找子文件夹, 'RegExp：查找规则')
  routeFiles.keys().forEach((key) => {
    // 1.2导入路由对象
    const route = require('@/route/userMenus' + key.split(.)[1])
    // 1.2.1获取的route为Module，其difault值才是路由对象
    allRouter.push(route.default) 
  })
  
  // 2.根据角色菜单递归获取要添加的路由对象
  const _recourceGetRoute = (menus) => {
    for(const menu of menus) {
      if(!menu.children){
        const route = allRoutes.find((route)=>route.path === menu.path)
        if(route) routes.push(route) // 匹配到对应的路由对象
      }else {
        // 递归循环children，直到没有children为止
        _recourceGetRoute(menu.children)
      }
    }
  }
 _recourceGetRoute(userMnues)
  return routes
}

export { firstMenu }

// 在对应时机进行动态路由注册（例如登录成功，获取到角色菜单之后）
import mapMenusToRoutes from '@/utils/mapMenus'
import router form '@/router'

const routes = mapMenusToRoutes(userMenus)
routes.forEach((route) => {
  router.addRoute('父级路由', route)
})

//在routes文件夹中路由守卫中跳转
import { firstMenu } from '@/utils/mapMenus'
router.beforeEach((to) => {
  if(to.path === '/main'){
    return firstMenu.path
  }
})
```

