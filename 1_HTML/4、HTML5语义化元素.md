# HTML5



## 1、HTML5 新增的语义化元素

- header：头部元素
- nav：导航元素
- section：定义文档某个区域的元素
- article：内容元素
- aside：侧边栏元素
- footer：尾部元素



## 2、HTML 其他新增元素

- audio：音频

  - 常见属性：url、height、width、controls、autoplay、muted、preload、poster
  - 支持的音频格式：https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Audio_codecs

- video：视频

  - 支持的视频格式：3GP、ADTS、FLAC、MPEG（2、4）、Ogg、MOV、WebM

  - video 兼容性写法

    ```html
    <video src="xxx"> <source src="xxx"></source></video>		
    ```



## 3、input 元素的扩展

- placehodler：输入框的占位
- multiple：开启多选
- autofocus：自动聚焦
- type值得扩展
  - date
  - time
  - number
  - tel
  - color
  - email
- MDN文档：https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/Input



## 4、新增全局属性 data-*

- data 设置的属性可以再 JavaScript 的 DOM 操作中通过 dateset 轻松获取到
- data-* 通常用于 HTML 和 JavaScript 数据之间的传递

