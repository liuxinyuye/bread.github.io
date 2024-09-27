---
title: swiper组件 轮播图
date: 2024-09-27 10:59:41
tags:
---
## 1. Swiper组件
Swiper组件提供滑动轮播显示的能力，针对复杂页面场景，可以使用Swiper组件的预加载机制，利用主线程的空闲时间来提前构建和部署绘制组件。

## 2. Swiper组件使用案例：
 **使用案例：** 
```
 Swiper() {
       Text($r('app.string.hello_message'))
         .fontSize(25)
         .margin(30)
         .fontWeight(FontWeight.Bold)
       Text($r('app.string.class_message'))
         .fontSize(25)
         .margin(30)
         .fontWeight(FontWeight.Bold)
     }
     .autoPlay(true)
     .loop(true)
}
```
![轮播模拟](https://foruda.gitee.com/images/1726192636932988734/6a3821a6_484447.png "屏幕截图")

## 3. ForEach 循环渲染
ForEach接口基于数组类型数据来进行循环渲染，需要与容器配合使用，且接口返回的组件应当是允许包含在ForEach父容器中的子组件。

```
ForEach(
        this.simpleList, 
        (item: string) => {ChildItem({ item: item })}, 
        (item: string) => item
       )
```

## 4. 利用Swiper组件，以及ForEach接口，完成轮播图的编写
#### 思路：
-   **由于在页面中的每一个轮播图，实际上包含着图片id、图片加载地址、图片点击后跳转的地址，这三个主要属性，所以我们先将轮播图的特点归纳成为一个统一的轮播图类。创建轮播图类：** 

```
class BannerClass {
  //字段
  id: string = '';
  imageSRC: ResourceStr = '';
  url: string = '';

  //构造函数 
  constructor(id: string, imageSrc: ResourceStr, url: string) {
    this.id = id;
    this.imageSRC = imageSrc;
    this.url = url;
  }
}
```
 **相关知识点：** TypeScript中类的创建

-  **创建数组类型的轮播图数据，由于项目中有6个轮播图，每个轮播图代表着一个轮播图对象（轮播图对象包含id、图片加载地址、图片点击后跳转地址），所以我们要创建6个轮播图对象，并且将这6个对象保存在数组中。** 

```
  @State bannerList: Array<BannerClass> = [
    new BannerClass('pic0',$r('app.media.banner_pic0'),''),
    new BannerClass('pic1',$r('app.media.banner_pic1'),''),
    new BannerClass('pic2',$r('app.media.banner_pic2'),''),
    new BannerClass('pic3',$r('app.media.banner_pic3'),''),
    new BannerClass('pic4',$r('app.media.banner_pic4'),''),
    new BannerClass('pic5',$r('app.media.banner_pic5'),'')
  ];
```
**相关知识点：** TypeScript中的数组

-  **由于是多图片轮播效果，这里我们使用Swiper组件实现效果。我们使用ForEach接口循环渲染上一步创建的轮播图数组数据，将多个轮播图渲染进Swiper组件中，并设置Swiper组件的loop属性为true，autoPlay属性为true，达到自动循环轮播的效果。** 

```
Swiper() {
      ForEach(this.bannerList,(item: BannerClass, index: number) => {
        Image(item.imageSRC)
          .objectFit(ImageFit.Contain)
          .width('100%')
          .padding({top: 11, left: 16, right: 36})
          .borderRadius(16)
      },(item: BannerClass, index: number) => item.id)
    }
    .autoPlay(true)
    .loop(true)
    .indicator(
      new DotIndicator()
        .color('#1a000000')
        .selectedColor('0A59F7')
```

