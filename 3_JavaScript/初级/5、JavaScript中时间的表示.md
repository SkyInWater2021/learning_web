# JavaScript 中时间的表示



## 1、创建 Date 的方式

```js

// 1. 无参数，获取当前的时间
const date = new Date()

// 2. 传入参数：时间字符串
const date = new Date('2022-05-23')

// 3. 传入参数：年月日时分秒毫秒
const date = new Date('2022','05','23','00','00','00','000')

// 4. 传入参数：时间戳（ Unix 时间戳 1970-01-01 00:00:00 到现在所经历的毫秒数）
const date = new Date('时间戳')

```



## 2、dateString 的表示标准

- 日期的表示方式有两种：RFC 2822 标准和 ISO 8601 标准
- 默认的 Date 对象是用的 RFC 2822标准
- ISO 8601 标准
  - YYYY：年份，0000~9999
  - MM：月份，01~12
  - DD：日，01-31
  - T：分隔日期和时间，没有特殊含义
  - HH：小时，00~24
  - mm：分钟，00~59
  - ss：秒钟，00~59
  - .sss：毫秒，000~999
  - Z：时区



## 3、dateString 标准的转化

```js
const date = new Date()

date.toDateString() 
date.toISOString() 

/* date 对象中获取信息的方法 */
date.getFullYear() // 获取年份（4位数）
date.getMouth() // 获取月份（0~11）
date.getDate() // 获取日（0~31）
date.getHours（） // 获取小时
date.getMinutes（） // 获取分钟
date.getSeconds（） // 获取秒钟
date.getMilliseconds // 获取毫秒数
date.getDay() // 获取一周中的第几天(0~6)

/* 也可以给 date 对象设置日期*/
date.setFullYear() 
date.set...

/* 获取时间戳 */
const timestamp = Date.now() // 当前时间的时间戳
const timestamp1 = date.getTime() || date.valueOf 获取 date 对象的时间戳

+date // 将 date 对象放到一个表达式里面，也可以实现转化为时间戳

/* Date.parse方法 从一个字符串中读取日期，并输出 unix 时间戳，无法解析时返回 NAN */
Date.parse(str) 作用等同于 new Date（dateString.getTime()

```

