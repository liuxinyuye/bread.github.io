---
title: ArtUI组件
date: 2024-09-27 11:07:11
tags:
---
## 自定义组件-构建单个item视图
我们在编写界面的时候，可以将常用的、重复的ArkUI组件，组合成为一个新的组件，方便重复调用，例如，消息列表。
![消息列表](https://foruda.gitee.com/images/1726220056386632235/ea57b956_484447.png "屏幕截图")

其中单个item视图：
![item视图分析](https://foruda.gitee.com/images/1726220120823018102/e5d6c625_484447.png "1718887180121.png")

这里我们将Row、Column、Text、Image组件组合成为一个新的模块，案例代码如下：
 
```
Row(){
      Column(){
        Text(this.tutorialItem.title)
          .height(19)
          .width('100%')
          .fontSize(14)
          .textAlign(TextAlign.Start)
          .textOverflow({overflow: TextOverflow.Ellipsis})
          .maxLines(1)
          .fontWeight(400)
          .margin({top: 4})
        Text(this.tutorialItem.brief)
          .height(32)
          .width('100%')
          .fontSize(12)
          .textAlign(TextAlign.Start)
          .textOverflow({overflow: TextOverflow.Ellipsis})
          .maxLines(2)
          .fontWeight(400)
          .margin({top: 4})
      }
      .height('100%')
      .layoutWeight(1)
      .alignItems(HorizontalAlign.Start)
      .margin({right: 12})

      Image(this.tutorialItem.imageSrc)
        .height('100%')
        .width(108)
        .borderRadius(16)
        .objectFit(ImageFit.Cover)
    }
    .width('100%')
    .height(88)
    .borderRadius(16)
    .backgroundColor(Color.White)
    .padding(12)
    .alignItems(VerticalAlign.Top)
```
## 父组件中数据导入到子组件中
#### 使用`@Prop`装饰器：父子单向同步
@Prop装饰的变量可以和父组件建立单向的同步关系。@Prop装饰的变量是可变的，但是变化不会同步回其父组件。

> @Prop装饰的变量和父组件建立单向的同步关系：
> - @Prop变量允许在本地修改，但修改后的变化不会同步回父组件。
> - 当数据源更改时，@Prop装饰的变量都会更新，并且会覆盖本地所有更改。因此，数值的同步是父组件到子组件（所属组件)，子组件数值的变化不会同步到父组件。
 **案例代码如下：** 
![Prop装饰器](https://foruda.gitee.com/images/1726221280278814675/e5e3e24c_484447.png "屏幕截图")

#### `@Prop`装饰器使用限制
- @Prop装饰变量时会进行深拷贝，在拷贝的过程中除了基本类型、Map、Set、Date、Array外，都会丢失类型。例如PixelMap等通过NAPI提供的复杂类型，由于有部分实现在Native侧，因此无法在ArkTS侧通过深拷贝获得完整的数据。
- @Prop装饰器不能在@Entry装饰的自定义组件中使用。

