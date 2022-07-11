## 一、Windows 环境下安装 Node（2022.4.20）



### 1、下载地址：http://nodejs.cn/download/

### 2、安装步骤：

- 选择安装路径、傻瓜式安装

- npm -v 查看npm版本

- node -v 查看node版本

- 在node安装路径（含node_modules的文件夹）下创建两个文件夹 node_global 和 node_cache

- 控制台执行命令

  ```shell
  npm config set prefix '安装路径\node_global'
  npm config set cache '安装路径\node_cache'
  ```
  

### 3、配置环境变量：

- 系统变量：NODE_PATH 设置为 `安装路径\node_modules `

- 用户环境变量：将 `XXX\AppData\Roming\npm` 改为  `安装路径\node_global`

- 执行 npm install xxx -g 全局安装时，即安装在 `安装路径\node_global `路径下

## 二、MacOS 环境下安装 Node

### 1、下载地址：http://nodejs.cn/download/

### 2、安装步骤：

- 傻瓜式安装即可

