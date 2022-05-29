

# MacOS 系统基本使用



## 1、习惯设置：

- 键盘映射更改：外接 window 键盘时使用键盘


- 鼠标滚动方向设置：系统偏好设置/鼠标/滚动方向:自然滚动勾选去掉
- 



## 2、常用的快捷键

- 查看隐藏文件：⇧ + ⌘  + . 
- 



## 3、MacOS 系统中使用 Homebrew

- 安装：

  ```shell
  // 别人写好的脚本  https://zhuanlan.zhihu.com/p/111014448
  /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
  ```

- 配置国内镜像源：
- 镜像源地址还原：



## 4、MacOS 生成秘钥链接 github 仓库

- 检查是否已连接：ssh -T git@github.com

- 生成秘钥：在终端输入 ssh-keygen -t rsa -C "xxx@xx.com"
- 一直点确定就行
- 将 隐藏文件 .ssh中的 id_rsa.pub 中的内容复制到 github 的秘钥中
