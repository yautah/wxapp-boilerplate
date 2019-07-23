# wxapp-boilerplate

> 小程序开发启动框架

## 说明

> 暂无

## 使用方式

> 1. 模块化。微信的全局函数及所有 api 已封装至 src/utils/wxp.js 中，这也更符合 es6 的模块化规范。wxp 中仍持有 wx 的一个引用，以应对一些没有涵盖的调用方式。（代码中未经引用直接使用 wx.xxx,或者 getApp()将会无法通过 lint。）示例：

```javascript
import wxp from 'libs/wxp.js'

console.log(wxp.app) //等同于原生的getApp()

console.log(wxp.getCurrentPages()) //等同于原生的getCurrentPages()

wxp.getSystemInfo().then(res => console.log(res)) //promise方式调用wx api

wxp.wx.getSystemInfoSync() //特殊情况下仍使用wx应用来调用同步函数
```

> 2. 引入 dva 及 redux。引入后小程序的启动流程如下：

![](http://git.wfxiao.com.cn/front/o2oadmin/raw/7acae137abd4e60e8b81bfb403b61ba9ac3c3157/docs/wxapp.png)


> 3. 项目已启用 prettier 及 eslint，git commit的时候会有eslint的commit hook检查，不遵循elsint的代码编写只能是“写时一时爽，提交头老大”，尽情享受规范带来的好处吧。
