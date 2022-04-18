# 基本安装步骤



## 1、下载地址：http://nodejs.cn/download/



## 2、安装步骤：

- ##### 选择安装路径、傻瓜式安装

- ##### npm -v 查看npm版本

- ##### node -v 查看node版本

- ##### 在node安装路径下（含node_modules文件夹）创建两个文件夹

- ##### node_cache 和 node_global

  ```shell
  npm config set prefix '安装路径\node_global'
  npm config set cache '安装路径\node_cache'
  ```



## 3、配置环境变量：

- ##### 系统变量：NODE_PATH 设置为 ' 安装路径\node_modules '

- ##### 用户环境变量：将 'XXX\AppData\Roming\npm ' 改为  ' 安装路径\node_global'

- ##### npm install XXX -g 即可全局安装