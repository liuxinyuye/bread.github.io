---
title:  UIAbility组件
date: 2024-09-27 10:55:40
tags:
cover:  https://ooo.0x0.ooo/2024/09/27/O4H8zs.jpg
---
### 相关概念
- UIAbility：UIAbility组件是一种包含UI界面的应用组件，主要用于和用户交互。UIAbility组件是系统调度的基本单元，为应用提供绘制界面的窗口；一个UIAbility组件中可以通过多个页面来实现一个功能模块。每一个UIAbility组件实例，都对应于一个最近任务列表中的任务。
- 自定义组件的生命周期：自定义组件的生命周期回调函数用于通知用户该自定义组件的生命周期，这些回调函数是私有的，在运行时由开发框架在特定的时间进行调用，不能从应用程序中手动调用这些回调函数。
- 窗口开发指导：窗口模块用于在同一块物理屏幕上，提供多个应用界面显示、交互的机制。

### 创建UIAbility组件
![UIAbility组件](https://foruda.gitee.com/images/1725609256692957369/ed2a9c3c_484447.png "屏幕截图")

### 创建编写Text组件

案例代码参考（将Text组件创建在build函数中，并且编写在Column组件之下）

```
build() {
    Column() {
      Text($r('app.string.hello_message'))
        .fontSize(CommonConstants.DEFAULT_FONT_SIZE)
        .fontColor(this.textColor)
        .margin(CommonConstants.DEFAULT_MARGIN)
        .fontWeight(FontWeight.Bold)
      Text($r('app.string.class_message'))
        .fontSize(CommonConstants.DEFAULT_FONT_SIZE)
        .fontColor(this.textColor)
        .margin(CommonConstants.DEFAULT_MARGIN)
        .fontWeight(FontWeight.Bold)
    }
    .width(CommonConstants.FULL_WIDTH)
```

### 改写Text组件中的文字内容
主要操作：在resource文件夹下，寻找对应string.json同步改写其中的文字信息。
1. resource -> base -> element -> string.json
![输入图片说明](https://foruda.gitee.com/images/1725609826911855498/018fba86_484447.png "屏幕截图")
2. resource -> en_US -> element -> string.json

3. resource -> zh_CN -> element -> string.json