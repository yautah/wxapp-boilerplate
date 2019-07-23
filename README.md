# tankB

> 小拼课 B 端小程序

## 说明

> 从 dva 核心包中单独打包 dva.js，已集成至项目

## 使用方式

###### 1. 模块化。微信的全局函数及所有 api 已封装至 src/libs/wxp.js 中，这也更符合 es6 的模块化规范。wxp 中仍持有 wx 的一个引用，以应对一些没有涵盖的调用方式。（代码中未经引用直接使用 wx.xxx,或者 getApp()将会无法通过 lint。）示例：

```javascript
import wxp from 'libs/wxp.js'

console.log(wxp.app) //等同于原生的getApp()

console.log(wxp.getCurrentPages()) //等同于原生的getCurrentPages()

wxp.getSystemInfo().then(res => console.log(res)) //promise方式调用wx api

wxp.wx.getSystemInfoSync() //特殊情况下仍使用wx应用来调用同步函数
```

###### 2. 引入 dva 及 redux。引入后小程序的启动流程如下：

![](http://git.wfxiao.com.cn/front/o2oadmin/raw/7acae137abd4e60e8b81bfb403b61ba9ac3c3157/docs/wxapp.png)

###### 3. 目录结构及规划。为了尽可能的利用小程序的分包特性，同时避免在使用 dva 过程中造成 model 命名污染。项目结构有如下要求：

*   a. 暂时不做分包，但是组件、model、接口 server 文件遵循以下原则：通用组件，model，services 文件在主包中，否则则一律划分到分包，便于之后做分包后的迁移。
*   b. 分包内目录内结构：
    ![](http://git.wfxiao.com.cn/front/o2oadmin/raw/7acae137abd4e60e8b81bfb403b61ba9ac3c3157/docs/subpackage.png)
*   c. page 目录内结构：
    ![](http://git.wfxiao.com.cn/front/o2oadmin/raw/7acae137abd4e60e8b81bfb403b61ba9ac3c3157/docs/pages.png)

###### 4. 项目已启用 prettier 及 eslint，尽情享受规范带来的好处吧。
