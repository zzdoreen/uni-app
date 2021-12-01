---
title: uni-app
date: 2021-11-15 15:16:00
categories:
- uni-app
---

## 文件目录结构

![](https://s3.bmp.ovh/imgs/2021/11/06f4e01c368b5249.png)

## 生命周期

### 应用生命周期  - App.vue

| 函数名 |说明 |
|----|----|
|onLaunch |当`uni-app` 初始化完成时触发（全局只触发一次）|
|onShow|当 `uni-app` 启动，或从后台进入前台显示|
|onHide|当 `uni-app` 从前台进入后台|
|onError|当 `uni-app` 报错时触发|
|onUniNViewMessage|对 `nvue` 页面发送的数据进行监听，可参考 nvue 向 vue 通讯|
|onUnhandledRejection|对未处理的 Promise 拒绝事件监听函数（2.8.1+）|
|onPageNotFound|页面不存在监听函数|
|onThemeChange|监听系统主题变化|

### 页面生命周期

|函数名	|说明	|平台差异说明	|最低版本|
|----|----|----|----|
|onInit	|监听页面初始化，其参数同 onLoad 参数，为上个页面传递的数据，参数类型为 Object（用于页面传参），触发时机早于 onLoad	|百度小程序	|3.1.0+|
|onLoad	|监听页面加载，其参数为上个页面传递的数据，参数类型为 Object（用于页面传参），参考示例||		
|onShow	|监听页面显示。页面每次出现在屏幕上都触发，包括从下级页面点返回露出当前页面||		
|onReady|	监听页面初次渲染完成。注意如果渲染速度快，会在页面进入动画完成前触发||		
|onHide|	监听页面隐藏		||
|onUnload|	监听页面卸载		||
|onResize|	监听窗口尺寸变化|	App、微信小程序	||
|onPullDownRefresh	|监听用户下拉动作，一般用于下拉刷新|||		
|onReachBottom|	页面滚动到底部的事件（不是scroll-view滚到底），常用于下拉下一页数据。具体见下方注意事项|||		
|onTabItemTap|	点击 tab 时触发，参数为Object，具体见下方注意事项|	微信小程序、QQ小程序、支付宝小程序、百度小程序、H5、App||	
|onShareAppMessage|	用户点击右上角分享	微信小程序、QQ小程序、支付宝小程序、字节小程序、飞书小程序、快手小程序||	
|onPageScroll|	监听页面滚动，参数为Object|	nvue暂不支持||	
|onNavigationBarButtonTap|	监听原生标题栏按钮点击事件，参数为Object|App、H5|	
|onBackPress	|监听页面返回，返回 event = {from:backbutton、 navigateBack} ，backbutton 表示来源是左上角返回按钮或 android 返回键；navigateBack表示来源是 uni.navigateBack ；详细说明及使用：onBackPress 详解。支付宝小程序只有真机能触发，只能监听非navigateBack引起的返回，不可阻止默认行为。|	app、H5、支付宝小程序	||
|onNavigationBarSearchInputChanged|	监听原生标题栏搜索输入框输入内容变化事件	|App、H5	|1.6.0|
|onNavigationBarSearchInputConfirmed|	监听原生标题栏搜索输入框搜索事件，用户点击软键盘上的“搜索”按钮时触发。	|App、H5	1.6.0|
|onNavigationBarSearchInputClicked|	监听原生标题栏搜索输入框点击事件（pages.json 中的 searchInput 配置 disabled 为 true 时才会触发）	|App、H5|	1.6.0
|onShareTimeline|	监听用户点击右上角转发到朋友圈|	微信小程序	|2.8.1+|
|onAddToFavorites	|监听用户点击右上角收藏	|微信小程序|	2.8.1+|

## 路由

> 跳转方式：`navigator`组件跳转(`声明式`)、调用`API`跳转(`编程式`)

```html
<navigator url="/pages/404/index">404</navigator>
```

```javascript
uni.navigateTo({ url: "/pages/index/index" });

/**
 * open-type属性 
 * 值：
 *  navigate - 打卡新页面
 *  redirectTo - 页面重定向
 *  navigateBack - 页面返回
 *  switchTab - tab切换
 *  reLaunch - 重加载
 **/
```

> tab切换 - 调用API`uni.switchTab`、使用组件`<navigator open-type="switchTab"/>`

### 路由传参与接收

> 传参

```javascript
uni.navigateTo(url:'page?name=doreen&age=18')
```

> 接收

```javascript
onLoad:function(option){
    console.log(option.name,option.age)    
}
```

## [页面配置](https://uniapp.dcloud.io/collocation/pages?id=%e9%85%8d%e7%bd%ae%e9%a1%b9%e5%88%97%e8%a1%a8)
> 在`pages.json`内配置页面路由

```json
"pages": [ 
    //pages数组中第一项表示应用启动页，参考：https://uniapp.dcloud.io/collocation/pages
    {
        "path": "pages/index/index",
        "style": {
            "navigationBarTitleText": "uni-app"
            }
    },
    {
        "path": "pages/404/index",
        "style": {
            "navigationBarTitleText": "页面不存在",
            "enablePullDownRefresh": false
            }
    }
],
```

#### pages配置项
|属性|类型|子属性|子类型|默认值|描述|
|----|----|----|----|----|----|
|path|string|||
|[style](https://uniapp.dcloud.io/collocation/pages?id=style)|Object|||
|||navigationBarBackgroundColor|HexColor|#000000|导航栏背景颜色|
|||navigationBarTextStyle|String|white|导航栏标题颜色及状态栏前景颜色，仅支持 black/white|
|||navigationBarTitleText|String||导航栏标题文字内容|
|||navigationBarBackgroundColor|HexColor|#000000|导航栏背景颜色|
|||……||||

#### tabBar配置项

|属性|类型|必填|默认值|描述|
|----|----|----|----|----|
|color|HexColor|是||tab上文字默认颜色|
|selectedColor|HexColor|是||tab上文字选中时的默认颜色|
|backgroundColor|HexColor|是||tab的背景色|
|list|Array|是||tab的列表，2-5个|

> list对象属性如下：

|属性|类型|必填|说明|
|----|----|----|----|
|pagePath|String|是|页面路径，必须在pages中先定义|
|text|String|是|tab上按钮文字|
|iconPath|String|否|图片路径|
|selectedIconPath|String|否|选中时的图片路径|
|visible|Boolean|否|该项是否展示，默认展示|

`配置了tabBar之后list内的页面不能使用uni.navigateTo进行跳转，需要改成uni.switchTab`
`对于在list内的页面，使用<navigator url=''>进行跳转时要加上 open-type="switchTab" 属性`
