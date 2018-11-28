#### 写在前面 ####
  无论是前端/小程序,还是任何一项技术，肯定都会有一个积累与试错的过程。在这个过程中，尝试失败在所难免。但我们也不能因此丧失勇气。在参考想过文档后，大胆的去尝试，努力分析出错的原因，久而久之便能迅速找到出错的地方了。
#### 常规布局 ####
  盒模型是静态页面的一个核心概念。在一个前端页面里，元素通过标签的形式来书写，每一个标签便是一个盒子，从上至下依次排序，最终构成整个文档。这时就会产生一个问题，有时我们需要让两列元素并排展示，有时我们希望一个元素里均匀嵌套三个子元素，在传统的布局形式中，我们需要通过浮动(float)或行级块(inline-block)来达到效果。但实际应用时会出现各种问题，尤其在涉及均分或按比例等分的时候，更是十分麻烦。这时我们就可以使用一种全新的布局方式：flex布局
#### flex ####
  flex布局是一种弹性盒子理念。在flex布局中，盒子的长度或者宽度可以伸缩的。这就给布局带来了极大的便利。下面我们就通过几个常用属性来探究一下flex布局。给一个元素加上display: flex;样式，它就变成了一个弹性盒子。
#### flex-direction ####
  属性值
  - column
  - column-reverse
  - row
  - row-reverse
  弹性盒子有一个主轴和一个交叉轴，可以想象成是两个相互垂直的坐标轴。flex-direction属性设置的是主轴的方向。默认为row。如果我们想让一个盒子的内部元素从左到右呈一行排列，就可以使用flex-direction: row;样式，同理，如果我们希望一个元素的所有子元素按纵向排列，就一个使用flex-direction: column;样式
#### flex-grow ####
  所谓弹性盒子，当一个元素盒子在主轴方向上的长度/宽度之和不足以占满它的长度/宽度时，或没有指定子元素的长度/宽度值，子元素应按照一定的比例拉伸以填充满父级元素，每一个flex-grow属性就是一个比例，如果比例均为1，便是1:1等分。
#### justify-content ####
  属性值
  - flex-start：左对齐 （默认值）
  - flex-end：右对齐
  - center： 居中
  - space-between：两端对齐，项目之间的间隔都相等。
  - space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
  有时我们不希望子元素盒子占满整个父元素，而是希望它们按照一定的方式在主轴上排列，这就用到了justify-content属性，这个属性指定了盒子在主轴上的排列方式
#### align-items ####
  属性值
  - flex-start：交叉轴的起点对齐。
  - flex-end：交叉轴的终点对齐。
  - center：交叉轴的中点对齐。
  - baseline: 项目的第一行文字的基线对齐。
  - stretch：如果项目未设置高度或设为auto，将占满整个容器的高度。（默认值）
  同上面一样，元素在交叉轴上也应该有一个对齐方式，这个属性便是指定元素在交叉轴上的对齐方式的。
#### 代码示例 ####
  flex布局的具体用法如下，将父元素的`display`CSS属性设置为` flex`并添加`flex-direction`属性。 `flex-grow`属性添加给子元素。下面这个页面集中展示了以上几个属性的效果[预览flex布局的效果](https://user65536.github.io/wiki-in-bupt/flex.html)
```
  .flex-column {
    width: 100px;
    height: 300px;
    background-color:aquamarine;
    display: flex;
    flex-direction: column;
  }
  .flex-column .item {
    flex-grow: 1;
    text-align: center;
    line-height: 98px;
    color: rgb(75, 150, 125) ;
    border: 1px solid rgb(75, 150, 125);
  }
  
```
```
  <div class="flex-column">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
  </div>

```

#### 组件库 ####
[iView Weapp](https://weapp.iviewui.com/docs/guide/start)是一个十分好用的小程序组件库。它将一些常用页面结构和样式封装好行程一个个组件，在使用时我们只需要写一个标签，就能实现一些复杂的功能。我们可以通过下面这个小程序预览组件的效果
![iView 小程序](./iView.jpg)

#### 准备工作 ####
[iView Weapp官方文档](https://weapp.iviewui.com/docs/guide/start)提供了快速开始的方案，我们在此基础上进行解读。
作为一个外部文件，我们首先要将组件库引入。进入IView的[Github](https://github.com/TalkingData/iview-weapp)页面，找到下载按钮。如果使用git命令下载，则点击复制链接地址，然后再本地运行git clone 命令下载。如果对git操作还不是很熟悉的话，可以下载zip文件然后解压。
![gitgub](./git.png)
下载好了之后，我们找到其中的`dist`文件夹，并将其复制到项目根目录下，就是`app.json`等文件所处的那个文件夹。在需要引用组件的页面的json文件里，我们添加这样一个属性
```
"usingComponents": {
    "i-button": "../../dist/button/index"
}
```
注意，这是json里的一个属性。所以如果你的json文件中没有其它属性时，它是这样的
```
{
  "usingComponents": {
    "i-button": "../../dist/button/index"
  }
}
```
在这里，usingComponents属性告诉小程序当前页面要使用组件，`i-button`是一个自定义的名字，这里定义成什么，页面里就写什么标签。在它的后面便是引用组件的路径。我们下载了组件库并将dist文件夹复制了下来，组件文件肯定就在这里了。我们用相对路径的位置说明自己引用的组件在哪里，就可以使用了。
在wxml文件里，添加下面这样一个标签，就使用了组件库中的组件。标签名便是我们之前在json里面定义的`i-button`。
```
<i-button type="primary" bind:click="handleClick">这是一个按钮</i-button>
```

#### 那么就开始吧 ####
新建一个页面，在页面的wxml文件中填入以下代码
```
<i-tabs current="{{ current }}" color="#f759ab" bindchange="handleChange">
    <i-tab key="tab1" title="选项1"></i-tab>
    <i-tab key="tab2" title="选项2"></i-tab>
    <i-tab key="tab3" title="选项3"></i-tab>
</i-tabs>
```
页面的js文件中填入以下代码
```
Page({
  data: {
    current: 'tab1'
  },
  handleChange: function (e) {
    console.log(e)//打印事件源对象
    this.setData({
      current: e.detail.key
    })
  }
})
```
json文件写入以下代码
```
{
  "usingComponents": {
    "i-tabs": "../../dist/tabs/index",
    "i-tab": "../../dist/tab/index"
  }
}
```
这里我们需要读懂代码的含义了。首先在json文件的`usingComponents`属性中，我们定义了两个组件。分别是页面上部的导航栏和导航栏选项。然后我们在wxml中依照[官方文档](https://weapp.iviewui.com/components/tabs)的说明使用组件。最重要的就是理解js的部分
这个tabs组件通过一个名为current的数据绑定来确定当前选中的标签。`bindchange="handleChange"`这个属性意为绑定一个名为`handleChange`的函数，用于处理tab切换事件。在js文件就需要有一个handleChange函数。事件处理函数都会有一个事件源对象传入，就是代码中的e。通过打印我们可以发现，点击不用的选项，e.detail.key中的值会有所不同，所以我们通过setData来设置current的属性值为e.detail.key，从而实现了从逻辑层到视图层的数据传递。
效果图如下
![效果图](./tab.PNG)
官方文档给我们提供了大量的实例，我们可以一一尝试，找到最适合页面的组件。

#### 其它组件库 ####
小程序组件库还有很多，它们的使用方式基本是相同的，都要先从代码仓库下载组件库代码并引入到自己的项目中，再根据文档的示例在自己的页面里使用组件。下面我再介绍一个微信出品的组件库`WeUI`
#### WeUI ####

[weui](https://weui.io/)提供了与微信几乎一致的UI界面样式，应用于小程序中可以给用户带来更加流畅的体验。并且官方还提供了用于UI设计的[psd和sketch文件](https://developers.weixin.qq.com/miniprogram/design/#%E8%B5%84%E6%BA%90%E4%B8%8B%E8%BD%BD)，可以轻松做出UI图，更方便的进行前端开发。

#### 使用WeUI ####
[weUI组件库源码](https://github.com/Tencent/weui-wxss/)也托管在GitHub仓库中，点击前面连接进入Github页面后，下载项目文件至本地后，使用开发者工具打开文件夹内的`dist`目录,**不要打开整个项目文件夹**
![dist](./weui-dist.PNG)

在微信开发者工具中打开dist目录后，即可看到模拟器中显示的组件预览

![weui](./weui.PNG)

那如何在我们自己的项目中使用WeUI呢，WeUI与上面的组件库使用稍有不同，WeUI需要我们手动拷贝wxml代码到自己的页面，如果有需要的话，还需要拷贝wxss和js文件。下面我们以一个表单页面为例，看一下WeUI的使用方式

#### 开始使用 ####
由于dist下面example文件夹均为案例页面，我们最好不在其上面更改，而是新建我们自己的页面。按照惯例，这个页面路径我们设置为`pages/index/index`。在`app.json`中的pages数组下，增加一行
`"pages/index/index",`
到pages数组的第0位，如图所示，这样做的目的是是的小程序编译后默认显示我们新建的页面。编辑好后保存，开发者工具会自动为我们新建pages和index文件夹。模拟器上显示我们新建的页面
![新建页面](./new.PNG)

接下来我们选择一个example目录下的组件，比如`panel`，复制这个文件夹下的panel.wxml中的代码到刚才新建的页面wxml文件中，再次保存，即可发现页面有了变化。

![panel](./panel.PNG)

但是图片并没有显示出来，仔细分析wxml代码，我们会发现图片的src是用数据绑定的方式指定的，在这里我们可以尝试一下将src改为常规的字符串路径方式，在相应路径放一张自己的图片，即可显示图片

#### 注意 ####
WeUI使用时并没有采用using-components的引用组件方式，这就要求开发者有一定的wxml标签结构分析能力，开发难度要大一些，但同时使用上也更加灵活，我们可以在WeUI的基础上随意修改组件内部的样式，以符合项目需求。在实际使用时需酌情选择组件库。此外，WeUI样式能生效的原因是app.wxss中有一句`@import 'style/weui.wxss';`这行代码引入了weui.wxss文件，才使得组件库的样式可以作用到全局


#### 常见问题 ####
在效果没有按照预期出现时，不要不知所措。首先要把引用组件库到使用组件库的这一个过程理清楚，然后再分别考虑是哪一个环节出了问题。一开始我们要拷贝dist文件夹，那么拷贝到的地方是不是根目录呢，如果不是的话后面在使用组件库的时候就找不到这个组件了。在json里面声明的组件路径如果不正确也同样会出现相同的问题。其次json中声明的组件名称和wxml中使用的名称是否一致？最后，js里面绑定的函数和数据名是否一一对应？把这个过程理清楚，问题就能很快被我们发现。
