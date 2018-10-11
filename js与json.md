## JavaScript 基本语法示例 ##
---

#### 变量 ####

JS语言中通过var关键字来定义变量，同时定义多个变量时可以用逗号隔开，省略后面的var关键字，如
```
var a = 123;
var b = undefined,
    array = [1, 2, 3],
    object = {
        name: 'xjmeng'
    };
```

#### 数组 ####

JS中数组可以直接用方括号来表示，定义数组的方法与C++语言稍有不同。数组的每一个值之间使用英文逗号符号隔开
```
var array = [1, 2, 3, 4, 5];
var pages = [
    "pages/index/index",
    "pages/log/log"
];
```

#### 对象 ####

JS中对象的表示方法也十分简洁，一对大括号扩住属性名与属性值与属性名，一个属性名和属性值的组合叫一个键值对，对象的属性值可以是任意一种数据类型。
```
注意实际编程时不要使用中文属性名
var object = {
    "属性名" : "属性值",
    name : 'xjmeng',
    length : 3
}
```

#### JSON ####

json 的官方解释为 JavaScript Object Notation，是从JavaScript对象语法中演化而来的一种数据格式，其语法要求如下
- 每个json文件都至少要有一对大括号{},不表示任何数据
- 大括号内与上述对象内部类似，不同的键值对之间通过逗号隔开
- 与对象不同的是，json中属性名和字符串必须用双引号包裹

```
{
  "pages":[
    "pages/index/index"
  ],
  "window":{
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "#fff",
    "navigationBarTitleText": "WeChat",
    "navigationBarTextStyle":"black"
  }
}
```
