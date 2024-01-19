## 一、JS的简介

javascript是由ECMAScript（JavaScript语法）+DOM（页面文档对象模型）+BOM（浏览器对象模型）

### 1. js三种书写位置

分别为行内式、内嵌式和外部式。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!--    2.内嵌式的js-->
    <script>
        alert("页面即将被打开")
    </script>
    <!--    3.外部js-->
    <script src="day01.js"></script>
</head>
<body>
<!--1.行内式的js 直接写到元素内部-->
<input type="button" value="按钮" onclick="alert('按钮被点击')">
</body>
</html>
```

1. 行内式
   * 可以将单行或少量JS代码写在HTML标签的事件属性中(以on开头的属性)，如：onclick
   * 主要单双引号的使用：在HTML中我们推荐使用双引号，JS中我们推荐使用单引号
   * 可读性差
   * 引号易错
   * 特殊情况下使用
2. 内嵌式
   * 可以将多行代码写到\<script>标签中
   * 内嵌JS是学习时常用方式
3. 外部JS文件
   * 利用HTML页面代码结构化，把大量JS代码独立到HTML页面之外，既美观，也方便文件级别的复用
   * 引用外部JS文件的script标签中间不可以写代码
   * 适合于JS代码量比较大的情况

### 2. JS输入输出语句

| 方法             | 说明                           | 归属   |
| ---------------- | ------------------------------ | ------ |
| alter(msg)       | 浏览器弹出警示框               | 浏览器 |
| console.log(msg) | 浏览器控制台打印输出信息       | 浏览器 |
| prompt(info)     | 浏览器弹出输入框，用户可以输入 | 浏览器 |

### 3.变量

声明变量：**var** age；//声明一个名称为age的遍变量

* var是一个JS关键字，用来声明变量。使用该关键字声明变量后，计算机会自动为变量分配内存空间，不需要程序员管

### 4.转换为字符串的三种方式：

* toString
* String()强制转换
* 加号拼接

### 5.转化为数字型

* parseInt(String)函数，转为整数值
* parseFloat(String)函数，转为浮点数值
* Number()强制转换函数
* js隐式转换：str - 0；

### 6.执行过程

![](https://maostudy.oss-cn-hangzhou.aliyuncs.com/image/js%E6%89%A7%E8%A1%8C%E8%BF%87%E7%A8%8B.png)

### 7.标识符 关键字 保留字

标识符就是我们为变量取得名字

关键字就是JS本身已经使用了的字，不能再将它们充当变量名、方法名

保留字：就是预留的关键字，以后可能会变为关键字

### 8.switch

```js
switch (sum){
    case 1:
        console.log(1);
        break
    default:
        break
}
```

注意：switch中的匹配值是用的全等

switch和if else if的区别：

1. 一般情况下，他们两个语句可以互相替换
2. switch...case语句进行条件判断后直接执行到相应到相应的条件语句，效率更高
3. 分支少选择if...else，分支多选择switch

### 9.修改数组长度

```js
const sum2 = [1, 2, 3, 4, 5, 'nihao'];
console.log(sum2.length)   //6
sum2.length=10;            //修改数组长度为10
console.log(sum2.length)   //10
console.log(sum2[6])       //undefined
sum2[6]='add'
console.log(sum2[6])        //add

const sum=new Array()       //创建空数组对象
console.log(sum.length)     //0
for(let i=0;i<10;i++){      //使用循环依次为数组增加值
    sum[i]=i;
}
console.log(sum.length)     //10


```

### 10.全局变量和局部变量

1. 全局变量
   * 在全局作用域下的变量，在全局下都可使用
   * 如果在函数内部 没有声明直接赋值的变量也为全局变量（不建议使用）

2. 局部变量
   * 在函数内声明的变量
   * 函数形参也是局部变量

从执行效率来看全局变量

1. 全局变量只有浏览器关闭的时候才会销毁，比较占内存资源
2. 局部变量 当我们程序执行完毕就会销毁，比较节约内存资源

### 11.作用域

js没有块级作用域，如：if(){变量}，为块级作用域

### 12.预解析

JavaScript代码是由浏览器中的javaScript解析器来执行的。javaScript解析器来执行的。JavaScript解析器在运行javaScript代码的时候分为两步：**预解析**和**代码执行**。

* 预解析js引擎会把js里面所有的var还有function提升到当前作用域的最前面
* 代码执行 按照代码书写的顺序从上往下执行

1. 预解析分为 **变量预解析**（变量提升）和**函数预解析**（函数提升）
2. 变量提升 就是把所有的变量声明提升到最前面，但是不提升赋值操作
3. 函数提升 就是把所有的函数声明提升到最前面，但是不调用函数

### 13.创建对象

1. 利用字面量创建对象

   就是花括号{}里面包含了表达这个具体事物（对象）的属性和方法
   
   ```js
   // var people={};//创建了一个空对象
   var people = {
       name: '张三',
       age: 18,
       sex: '男',
       setHi: function () {
           return "你好"
       }
   }
   ```

2. 利用new Object创建对象

```js
var obj = new Object();
obj.name = '张三';
obj.age = 18;
obj.sex = '男';
obj.sayHi = function () {
    return "你好"
}
```

3. 利用构造函数创建对象
   //前面两种形式一次只能创建一个对象
   //里面封装的不是普通代码，而是封装的对象

```js
// function study(){
//   this.属性=值;
//   this.方法=function (){}
// }
//构造函数通过new调用    new构造函数名
function study(name, age, code) {
    this.name = name;
    this.age = age;
    this.code = code;
    this.info = function () {
        return "名字是：" + this.name + ",年龄是：" + this.age + ",学号是：" + this.code;
    }
}

var xiaoming = new study("小明", 18, "1646184615");
```

new关键字

1. 在内存中创建一个新的空对象
2. 让this指向这个新创建的对象
3. 执行构造函数里面的代码，给这个新对象添加属性和方法
4. 返回这个新对象（所以构造函数里面不需要return）

### 14.遍历对象

```js
var people = {
        name: '张三',
        age: 18,
        sex: '男',
        setHi: function () {
          return "你好"
        }
      }
      //使用for in遍历对象
      for(let k in people){
        console.log(k)
      }
```

### 15.Math

Math.ceil()向上取整
Math.round()四舍五入 就近取整
Math.floor()向下取整

### 16.检测是否是数组

instanceof运算符

```js
var arr=[];
var obj={};
console.log(arr instanceof Array);            //true
console.log(obj instanceof Array);            //false
```

isArray()

```js
var arr=[];
var obj={};
console.log(Array.isArray(arr));            //true
console.log(Array.isArray(obj));            //false
```

Array.isArray优先于instanceof

### 17添加删除元素

1. push在数组末尾添加一个或多个元素
2. unshift在数组开头添加一个或者多个元素
3. pop删除数组最后一个元素，有返回值
4. shift删除数组中第一个元素，有返回值

# WEb   APIs

Web API是浏览器提供的一套**操作浏览器功能**和**页面元素**的API(BOM和DOM)

## 一、DOM

文档对象模型
通过DOM这些接口可以改变网页内容、结构和样式

### 1.DOM树

![](https://maostudy.oss-cn-hangzhou.aliyuncs.com/image/DOM%E6%A0%91.png)

* 文档：一个页面就是一个文档，DOM中使用document表示
* 元素：页面中的所有标签都是元素，DOM中使用element表示
* 结点：网页中的所有内容都是节点（标签、属性、注释、文本），DOM中使用node表示

### 2.获取元素

* 根据ID获取

  使用getElementById()方法获取带有ID属性的元素对象

* 根据标签名获取

  使用getElementsByTagName（）方法获取指定标签名的元素对象

  返回的是 获取过来元素对象的集合 以伪数组的形式存储的

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="Hi">
      Hi,Welcome
  </div>
  <ul id="ul">
      <li>知否知否，应是等你好久</li>
      <li>知否知否，应是等你好久</li>
      <li>知否知否，应是等你好久</li>
      <li>知否知否，应是等你好久</li>
      <li>知否知否，应是等你好久</li>
  </ul>
  <script>
      //因为文档从上往下加载，所以先得有标签
  
      //根据ID获取
      //document.getElementById() 返回的是一个元素对象
      var hi = document.getElementById('Hi')
      console.log(hi);
      //console.dir打印我们的元素对象 更好的查看元素属性
      console.dir(hi)
  
      //根据标签名获取
      //返回的是 获取过来元素对象的集合 以伪数组的形式存储的
      var lis = document.getElementsByTagName('li')
      console.log(lis)
  
      //根据标签名获取
      //还可以获取某个父元素内部所有指定标签名的子元素
      //element.getElementsByTagName('标签名')
      //注意：父元素必须是单个对象（必须指明是哪一个元素对象）。获取的时候不包括父元素自己
      var ul=document.getElementsByTagName('ul')
      console.log(ul[0].getElementsByTagName('li'))
      //或者为ul指定id
      ul=document.getElementById('ul')
      console.log(ul.getElementsByTagName('li'))
  </script>
  </body>
  </html>
  ```

  

* 通过HTML5新增的方法获取

  1. getElementsByClassName ()；根据类名获取某些元素集合 ，返回元素对象集合
  2. querySelector()；根据指定选择器返回**第一个**元素对象
  3. querySelectorAll()；根据指定选择器返回

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div class="box">盒子1</div>
  <div class="box">盒子2</div>
  <div id="nav">
      <ul>
          <li>首页</li>
          <li>产品</li>
      </ul>
  </div>
  <script>
      //getElementsByClassName 根据类名获取某些元素集合
      var boxs = document.getElementsByClassName('box')
      console.log(boxs)
      //querySelector 根据指定选择器返回第一个元素对象
      var box1=document.querySelector('.box');
      console.log(box1)
      var nav=document.querySelector('#nav');
      console.log(nav)
      var li=document.querySelector('li')
      console.log(li)
  
      //根据指定选择器返回
      var box1=document.querySelectorAll('.box');
      console.log(box1)
      var nav=document.querySelectorAll('#nav');
      console.log(nav)
      var li=document.querySelectorAll('li')
      console.log(li)
  </script>
  </body>
  </html>
  ```

  

* 特殊元素获取

  1. 获取body元素

     ```js
     //1.获取body标签
         var bodyEle=document.body
         console.log(bodyEle)
         console.dir(bodyEle)
     ```

  2. 获取html元素

     ```js
     //获取html标签
         var htmlEle=document.documentElement;
         console.log(htmlEle)
     ```

### 3.事件基础

JavaScript使我们有能力创建动态页面，而事件是可以被JavaScript侦测到的行为
简单理解：触发---响应机制

```js
//1.事件由三部分组成 事件源 事件类型 事件处理程序 我们也称为事件三要素
    //（1）事件源 事件被触发的对象
    var btn = document.getElementById('btn');
    //(2)事件类型，如onclick
    //(3)事件处理程序
    btn.onclick = function () {
        alert("按钮被点击了")
    }
```

执行事件的步骤：

1. 获取事件源
2. 注册事件
3. 添加事件处理程序

### 4.操作元素

#### 4.1修改元素内容

* element.innerText：从起始位置到终止位置的内容，但他去除html标签，同时空格和换行也会失掉

* element.innerHTML：起始位置和终止位置的全部内容，包含html标签，同时保留空格和换行

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div, p {
            width: 300px;
            height: 30px;
            line-height: 30px;
            color: #88BBCC;
            background-color: #AAFF88;
        }
    </style>
</head>
<body>
<button>显示当前事件</button>
<div>某个时间</div>
<p>123</p>
<script>
    var btn = document.querySelector('button');
    var div = document.querySelector('div');
    btn.onclick = function () {
        div.innerText = getDate();
    }

    function getDate() {
        var date = new Date();
        var year = date.getFullYear();
        var month = date.getMonth() + 1;
        var dates = date.getDate();
        var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六']
        var day = date.getDay();
        return '今天是：' + year + '年' + month + '月' + dates + '日' + arr[day];
    }

    //也可以不用添加事件
    var p = document.querySelector('p')
    p.innerText = getDate();
</script>
</body>
</html>
```

区别：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div>某个时间</div>
<p>
    我是文字
    <span>123</span>
</p>
<script>
    //innerText和innerHTML区别
    //1.innerText
    var div = document.querySelector('div');
    //innerText不识别html标签，非标准
    div.innerText = '初始化'
    //innerHTML识别html标签，W3C标准
    div.innerHTML = '<Strong> 初始化 <Strong>'
    //这两个属性都是可读写的
    var p = document.querySelector('p');
    console.log(p.innerText)
    console.log(p.innerHTML)
</script>
</body>
</html>
```

#### 4.2修改元素属性

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
  <style>
    img{
      width: 100px;
    }
  </style>
</head>
<body>
<button id="one"></button>
<button id="two"></button>
<img src="https://maostudy.oss-cn-hangzhou.aliyuncs.com/image/logIcon.jpg" alt="" title="">
<script>
  var btn1=document.querySelector('#one')
  var btn2=document.querySelector('#two')
  var img=document.querySelector('img')
  btn2.onclick=function (){
    img.src='https://maostudy.oss-cn-hangzhou.aliyuncs.com/image/head.jpg';
  }
  btn1.onclick=function (){
    img.src='https://maostudy.oss-cn-hangzhou.aliyuncs.com/image/logIcon.jpg'
  }
</script>
</body>
</html>
```

#### 4.3表单元素的属性操作

利用DOM可以操作如下表单元素的属性：

type、value、checked、selected、disabled

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<button>按钮</button>
<label>
    <input type="text" value="输入内容">
</label>
<script>
    var btn = document.querySelector("button");
    var input = document.querySelector("input");
    btn.onclick = function () {
        // input.innerHTML='点击了';这个是普通盒子才能用
        //表单里面的值通过value改变
        input.value = "按钮被点击了";
        //按钮点击后就禁止再次点击
        // btn.disabled=true;
        this.disabled = true;
        //this指向当前函数的调用者
    }
</script>
</body>
</html>
```

#### 4.4样式属性操作

1. element.style      行内式样式操作

   **注意：**

   * JS里面修改样式采用驼峰命名法，比如FontSize
   * JS修改style样式操作，产生的是行内样式，css权重比较高

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>Title</title>
       <style>
           div {
               width: 300px;
               height: 200px;
               background-color: #88BBCC;
             transition: all 1s;
           }
       </style>
   </head>
   <body>
   <div></div>
   <script>
       var div = document.querySelector('div')
       div.onclick = function () {
           this.style.backgroundColor = 'purple';
           this.style.width='250px'
       }
   </script>
   </body>
   </html>
   ```

   

2. element.className 类名样式操作

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .change {
            width: 10px;
            height: 60px;
            background-color: #88BBCC;
            color: #cccccc;
            font-size: 25px;
            margin: 0 auto;
        }
    </style>
</head>
<body>
<div>文本</div>
<script>
    var text = document.querySelector('div');
    text.onclick = function () {
        this.className = 'change'
    }
</script>
</body>
</html>
```

**注意**：

* 如果样式修改较多，可以采取操作类名方式更改元素样式
* class因为是个保留字，因此使用className来操作元素类名属性
* className会直接修改元素的类名，会覆盖原来的类名

#### 4.5 对属性值更改

1. 获取自定义元素属性
   * element.属性 获取属性值
   * element.getAttribute(‘属性’)

区别：

* element.属性 获取内置属性值（元素本身自带的属性）
* element.getAttribute('属性');主要获得自定义的属性（标准）我们程序员自定义的属性

2. 设置移除自定义属性
   * element.属性='值' 设置内置属性值；（元素本身自带的属性
   * element.setAttribute(‘属性’，‘值’)；主要针对于自定义属性

3. 移除属性
   * element.removeAttribute(属性)

**H5规定自定义属性以data-开头作为属性名并且赋值**

**获取H5自定义属性**

* 兼容性获取：element.getAttribute('data-属性名')
* H5新增element.dataset.index或者element.dataset['index']   ie11才开始支持
  如果自定义属性中有多个-链接的单词，我们获取的时候采用 驼峰命名法

### 5.节点操作

获取元素常用两种方式：

1. 通过DOM提供的方法获取元素

   * ducument.getElementById()
   * document.getElementsByTagName()
   * document.querySelector等

   逻辑性不强，繁琐

2. 利用节点层级关系获取元素

   * 利用父子兄节点关系获取元素
   * 逻辑性强，但是兼容性稍差

#### 5.1节点概述

节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）三个基本属性

* 元素节点 nodeType=1
* 属性节点 nodeType=2
* 文本节点nodeType=3（包含文字、空格、换行等）

实际开发中，节点操作主要操作的是元素节点

#### 5.2节点层级

1. 父级层级

   element.parentNode  获得父节点

2. 子级层级

   element.childNodes（标准)   获得所有子节点

   **注意**：

   * **返回值里面包含了所有的子节点，包含元素节点、文本节点等**
   * **如果只想获得里面的元素节点，则需专门处理。所以一般不提倡使用childNodes**、

   elementNode.children（非标准） 获取所有**子元素节点**，实际开发中常用

   (1).获取第一个子节点：elementNode.firstChild

   (2).获取最后一个子节点：elementNode.lastChild

   (3)获取第一个**子元素**节点：elementNode.firstElementChild

   (4)获取最后一个**子元素**节点：elementNode.lastElementChild

   **注意：上面两个方法有兼容性问题，IE9以上才支持**

   实际开发中的写法：element.children[n]获取下标为n的**子元素**节点

3. 兄弟节点

   element.nextSibling   获取下一个兄弟节点
   element.previousSibling   获取上一个兄弟节点
   element.nextelementSibling   获取下一个兄弟**元素**节点
   element.previousElementSibling   获取上一个兄弟**元素**节点
   **注意：上面两个方法有兼容性问题，IE9以上才支持**

   解决兼容性问题：
   自己封装一个兼容性函数

   ```js
   function getNextElementSibiling(element){
       var el=element;
       while(el = el.nextSibling){
           if(el.nodeType===1){
               return el;
           }
       }
       return null;
   }
   ```

#### 5.3创建节点

document.createElement(‘li’)；

#### 5.4添加节点

node.appendChild(child)

在某元素前面插入一个元素
node.insertBefore(child,指定元素)
将一个节点添加到父节点的指定子节点前面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<ul>
    <li>123</li>
</ul>
<script>
    var li=document.createElement('li');
    var ul=document.querySelector('ul')
    ul.appendChild(li)
    var lili=document.createElement('li')
    ul.insertBefore(lili,ul.children[0]);
</script>
</body>
</html>
```

#### 5.5删除节点

node.removeChild(child)
从DOM中删除一个子节点，返回删除的节点

<a\>标签里面的href属性值为Javascript:;时表明禁止链接跳转

#### 5.6复制节点

node.cloneNode()
node.cloneNode()方法返回调用该节点的一个副本。也称为克隆节点

**注意：**

1. 如果括号参数为**空或者为false**,则为**浅拷贝**，即只克隆复制该节点本身，不克隆里面的子节点
2. 如果括号里面是**true**，则为**深拷贝** 复制标签复制里面的内容

#### 5.7三种动态创建元素的区别

* document.write()
* element.innerHTML
* document.createElement()

1. 如果页面文档流加载完毕，在调用该方法会导致页面重绘
2. innerHTML是将内容写入某个DOM节点，不会导致页面全部重绘
3. innerHTML创建多个元素效率更高（前提是使用数组模式拼接），结构稍微复杂
4. createElement()创建多个元素效率稍微低一些，但结构更加清晰

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
<button>点击</button>
<p>abc</p>
<div class="inner"></div>
<div class="create"></div>
<script>
    // window.onload = function() {
    //         document.write('<div>123</div>');

    //     }
    // 三种创建元素方式区别 
    // 1. document.write() 创建元素  如果页面文档流加载完毕，再调用这句话会导致页面重绘
    // var btn = document.querySelector('button');
    // btn.onclick = function() {
    //     document.write('<div>123</div>');
    // }

    // 2. innerHTML 创建元素
    var inner = document.querySelector('.inner');
    // for (var i = 0; i <= 100; i++) {
    //     inner.innerHTML += '<a href="#">百度</a>'
    // }
    var arr = [];
    for (var i = 0; i <= 100; i++) {
        arr.push('<a href="#">百度</a>');
    }
    inner.innerHTML = arr.join('');
    // 3. document.createElement() 创建元素
    var create = document.querySelector('.create');
    for (var i = 0; i <= 100; i++) {
        var a = document.createElement('a');
        create.appendChild(a);
    }
</script>
</body>
</html>
```

##  二、事件高级

### 1.注册事件（绑定事件）

注册方式有两种：**传统方式**和**方法监听注册方式**

1. **传统方式**：

* 利用on开头的事件onclick
* 特点：注册事件**唯一性**
* 同一个元素同一个事件只能设置一个处理函数，最后注册的处理函数会覆盖之前的处理函数

2. **方法监听注册方式**

* w3c标准推荐方式
* addEventListener()它是一个好方法
* IE9之前不支持此方法，可用attachEvent()代替
* 特点：同一个元素同一事件可以注册多个监听器
* 按注册顺序依次执行

**addEventListener事件监听方式**

eventTarget.addEventListener(type,listener[,useCapture])
eventTarget.addEventListener()方法将指定的监听器注册到eventTarget（目标对象）上，当该对象触发指定事件时，就会执行事件处理函数。

* **type**：事件类型字符串，比如click，mouseover，注意这里不能加on
* **listener**：事件处理函数，事件发生时，会调用该函数
* **useCapture**：可选参数，是一个布尔值，默认是false

### 2.删除事件

删除方式有两种 ：传统方式和

**传统方式**

eventTarget.onclick=null;

**方法监听注册方式**

1. eventTarget.removeEventListener(type,listener[,useCapture]);
2. 对于使用attachEvent注册的监听事件，需要使用detachEvent('type',listener)来删除

### 3.DOM事件流

**事件流**描述的是从页面中接收事件的顺序

**事件**发生时会在元素节点之间按照特定的顺序传播，这个**传播过程**即**DOM事件流**

DOM事件分为3个阶段：

1. 捕获阶段
2. 当前目标阶段
3. 冒泡阶段

注意：

1. JS代码中只能执行捕获或者冒泡中的一个阶段
2. onclick和attachEvent只能获取冒泡阶段
3. **捕获阶段** 如果addEventListener 第三个参数是 true 那么则处于捕获阶段  document -> html -> body -> father -> son
4. **冒泡阶段** 如果addEventListener 第三个参数是 false 或者 省略 那么则处于冒泡阶段  son -> father ->body -> html -> document

### 4.事件对象

1. event 就是一个事件对象 写到我们侦听函数的 小括号里面 当形参来看
2. 事件对象只有有了事件才会存在，它是系统给我们自动创建的，不需要我们传递参数
3. 事件对象 是 我们事件的一系列相关数据的集合 跟事件相关的 比如鼠标点击里面就包含了鼠标的相关信息，鼠标坐标啊，如果是键盘事件里面就包含的键盘事件的信息 比如 判断用户按下了那个键
4. 这个事件对象我们可以自己命名 比如 event 、 evt、 e
5. 事件对象也有兼容性问题 ie678 通过 window.event 兼容性的写法  e = e || window.event;

```js
// 事件对象
    var div = document.querySelector('div');
    div.onclick = function (e) {
        // console.log(e);
        // console.log(window.event);
        // e = e || window.event;
        console.log(e);
    }
    div.addEventListener('click', function (e) {
        console.log(e);
    })
```

常见属性和方法

| 事件对象属性方法  | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| e.target          | 返回**触发**事件的对象 标准                                  |
| e.srcElement      | 返回**触发**事件的对象 非标准 ie6-8使用                      |
| e.type            | 返回事件的类型 比如click mouseover 不带on                    |
| e.cancelBubble    | 该属性**阻止冒泡** 非标准ie6-8使用                           |
| e.returnValue     | 该属性 阻止默认事件（默认行为）非标准 ie6-8使用 比如不让链接跳转 |
| e.preventDefault  | 该方法阻止默认事件（默认行为）标准 比如不让连接跳转          |
| e.stopPropagation | **阻止冒泡** 标准                                            |

### 5.事件委托（代理、委派）

**原理**：

* 不是每个子节点单独设置事件监听器，而是事件监听器设置在其父节点上，然后利用冒泡原理影响设置每个子节点。

**作用**：

* 只操作了一次DOM，提高了程序的性能

### 6.常用的鼠标事件

1. 禁止鼠标右击菜单

```js
document.addEventListener('contextmeue',function(e){
    e.preventDefault();
})
```

2. 禁止鼠标选中

```js
document.addEventListener('selectstart',function(e){
    e.preventDefault();
})
```

| 鼠标事件对象 | 说明                                   |
| ------------ | -------------------------------------- |
| e.clientX    | 返回鼠标相对于浏览器窗口可视区的X坐标  |
| e.clientY    | 返回鼠标相对于浏览器窗口可视区的Y坐标  |
| e.pageX      | 返回鼠标相对于文档页面的X坐标 IE9+支持 |
| e.pageY      | 返回鼠标相对于文档页面的Y坐标 IE9+支持 |
| e.screenX    | 返回鼠标相对于电脑屏幕的X坐标          |
| e.screenY    | 返回鼠标相对于电脑屏幕的Y坐标          |

### 7.常用键盘事件

| 键盘事件   | 触发条件                                  |
| ---------- | ----------------------------------------- |
| onkeyup    | 某个键盘按键被松开时触发                  |
| onkeydown  | 某个键盘按键被按下时触发                  |
| onkeypress | 某个键盘按键被按下是 触发（不识别功能键） |

* keyup事件和keydown不区分字母大小写
* keypress事件区分大小写

注意：

1. keydown和keypress在文本框中的特点：他们两个事件触发的时候，文字还没有落入文本框中
2. keyup事件触发的时候，文本已经落入文本框里面了

## 三、BOM

### 1.概述

**浏览器对象模型****，它提供了独立于内容而**与浏览器窗口进行交互的对象**，其核心是window

BOM的组成

![](https://maostudy.oss-cn-hangzhou.aliyuncs.com/image/BOM%E7%9A%84%E6%9E%84%E6%88%90.png)

**window对象是浏览器的顶级对象**

1. 它是JS访问浏览器窗口的一个接口
2. 它是一个全局对象。定义在全局作用域中的变量和函数都会变成window对象得属性和方法

注意：**window下一个特殊的属性window.name**

### 2.窗口加载事件

window.onload=function(){}
或者
window.addeventListener("load",function(){});

window.onload是窗口加载事件，当文档内容完全加载完成会触发该事件，就调用的处理函数

**注意**：

* 有了window.onload就可以把js代码写到页面元素上方，因为onload是等页面内容全部加载完毕，再去执行处理函数
* window.onload传统注册方式只能写一次，如果有多个，会以最后一个window.onload为准
* 使用addeventListener则没有限制

window.addeventListener('DOMContentLoaded',function(){})

DOMContentLoaded事件触发时，仅当DOM加载完成，不包括样式表，图片，flash等等
Ie9以上才支持

### 3.调整窗口大小事件

window.onresize=function(){};
window.addeventListener('resize',function(){});

window.onresize是调整窗口大小加载事件，当触发时就调用的处理函数

**注意**：

* 只要窗口大小发送像素变化，就会触发这个事件
* 我们可以通过window.innerWidth获取当前屏幕宽度

### 4.定时器

#### 4.1开始定时

* **setTimeout**()
* **setInterval**()

1. window.setTimeout(调用函数，[延迟的毫秒数])

   setTimeout方法用于设置一个定时器，该定时器在定时器到期后执行调用函数。setTimeout（）我们也称为**回调函数callback**

2. window.setInterval(调用函数，[延迟的毫秒数])

   setInterval方法重复调用一个函数，每隔这个时间就去执行一次该回调函数

**注意:**

1. 这个window在调用的时候可以省略
2. 这个延时时间单位是毫秒 但是可以省略，如果省略默认的是0
3. 这个调用函数可以直接**写函数 或者写 函数名** 还有一个写法 '函数名()'
4.  页面中可能有很多的定时器，我们经常给定时器加标识符 （名字)

**区别：**

* setTimeout  延时时间到了，就去调用这个回调函数，只调用一次 就结束了这个定时器
* setInterval  每隔这个延时时间，就去调用这个回调函数，会调用很多次，重复调用这个函数

#### 4.2停止定时

window.clearTimeout(timeoutId)

### 5.this指向问题

```js
// this 指向问题 一般情况下this的最终指向的是那个调用它的对象

 // 1. 全局作用域或者普通函数中this指向全局对象window（ 注意定时器里面的this指向window）
console.log(this);

function fn() {
    console.log(this);
}
window.fn();
window.setTimeout(function() {
            console.log(this);
}, 1000);
// 2. 方法调用中谁调用this指向谁
var o = {
    sayHi: function() {
        console.log(this); // this指向的是 o 这个对象
    }
}
o.sayHi();
var btn = document.querySelector('button');
// btn.onclick = function() {
//     console.log(this); // this指向的是btn这个按钮对象
// }
btn.addEventListener('click', function() {
        console.log(this); // this指向的是btn这个按钮对象
})
// 3. 构造函数中this指向构造函数的实例
function Fun() {
    console.log(this); // this 指向的是fun 实例对象
}
var fun = new Fun();
```

### 6.JS执行机制

#### 6.1Js是单线程

同一时间只能做一件事，所有任务都需要排队。

#### 6.2同步和异步

为解决单线程问题，H5提出Web Worker，允许js脚本创建多个线程。
同步任务都放在**主线程**的**执行栈**中

异步任务是通过函数回调实现的
一般而言的异步任务有：

* 普通事件，click、resize等
* 资源加载：如load、error等
* 定时器，包括setInterval、setTimeout

JS执行机制：

1. 先执行**执行栈中的同步任务**
2. 异步任务放入任务栈
3. 一旦执行栈中的所有同步任务执行完毕，系统就会按次序读取**任务队列**中的异步任务，于是被读取的异步任务结束等待状态，进入执行栈，开始执行

### 7.location对象

window对象给我们提供一个**location属性**用于**获取或设置窗体的URL**，并且可以用于**解析URL**。因为这个属性返回的是一个对象，所以我们将这个属性也称为**location对象**

URL**统一资源定位符**

一般形式：protocal://host[:port]/path/[?query]#frament

location对象属性

| location对象属性  | 返回值            |
| ----------------- | ----------------- |
| location.herf     | 获取或设置整个URL |
| location.host     | 返回主机（域名）  |
| location.port     | 返回端口号        |
| location.pathname | 返回路径          |
| location.search   | 返回参数          |
| location.hash     | 返回片断          |

location对象方法

| location对象方法   | 返回值                                                       |
| ------------------ | ------------------------------------------------------------ |
| location.assign()  | 跟herf一样,可以跳转页面                                      |
| location.replace() | 替换当前页面，因为不记录历史，所以不能后退页面               |
| location.reload()  | 重新加载页面，相当于刷新按钮或者f5，若参数为true，则为强制刷新 |

### 8.navigator对象

navigator对象包含有关浏览器的信息，它有很多属性，我们最常用的是userAgent，该属性可以返回由客户机发送服务器的user-agent头部的值

### 9.history对象

| history对象方法 | 作用                                               |
| --------------- | -------------------------------------------------- |
| back()          | 后退功能                                           |
| forward()       | 前进功能                                           |
| go(参数)        | 前进后退功能，1表示前进1个页面，-1表示后退一个页面 |

 ## 四、PC端网页特效

### 1.offset

可以动态的得到该元素的位置（偏移）、大小等

* 可以获取元素距离带有定位父元素的位置
* 获取元素自身的大小(宽度、高度)
* 注意：返回的数值都不带单位

offset常用属性：

| offset系列属性       | 作用                                                        |
| -------------------- | ----------------------------------------------------------- |
| element.offsetParent | 返回作为该元素带有定位的父级 如果父级没定位则返回body       |
| element.offsetTop    | 返回元素相对带有定位的父元素上方的偏移量                    |
| element.offsetLeft   | 返回元素相对带有定位的父元素左边框的偏移                    |
| element.offsetWidth  | 返回自身包括padding、边框、内容区的宽度，返回数值不带单位   |
| element.offsetHeight | 返回自身包括padding、边框、内容区的宽高度，返回数值不带单位 |

offset和style区别

offset：

* offset可以得到任意样式表中的样式值
* offset获得的数值是没有单位的
* offsetWidth包含padding+border+width
* offsetWidth等属性是只读属性，只能获取不能赋值
* 所以，我们想要获取元素大小位置，用offset更合适

style:

* style只能获取行内样式表中的样式值
* style.width获得的是带有单位的字符串
* style.width获得不包含padding和border的值
* style.width是可读写属性，可以获取也可以赋值
* 所以改变样式，需要用style

### 2.client

用于动态获取该元素的边框大小、元素大小等

| client系列属性       | 作用                              |
| -------------------- | --------------------------------- |
| element.clientTop    | 返回元素上边框的大小              |
| element.clientLeft   | 返回元素左边框的大小              |
| element.clientWidth  | 返回自身包括padding、内容区的宽度 |
| element.clientHeight | 返回自身包括padding、内容区的高度 |

立即执行函数：(function(x，y)  { })(a,b)
主要作用：创建一个独立的作用域
后面括号中的值为传入的值，前面括号中的x，y为接收参数的值

### 3.scroll系列属性

可以动态的得到该元素大小、滚动距离等

| scroll系列属性       | 作用                         |
| -------------------- | ---------------------------- |
| element.scrollTop    | 返回被卷上去的上侧距离       |
| element.scrollLeft   | 返回被卷去的左侧距离         |
| element.scrollWidth  | 返回自身实际的宽度，不含边框 |
| element.scrollHeight | 返回自身实际的高度，不含边框 |

拖动滚动条就会触发的事件**onscroll**事件

mouseover和mouseenter的区别

* 当鼠标移动到元素上时就会触发mouseenter事件
* 类似mouseover
* 区别是mouseover鼠标经过自身盒子和子盒子都会触发，而mouseenter只在经过自身盒子时触发
* 原因是，mouseenter不会冒泡

### 4.动画原理

核心原理：通过定时器setInterval()不断移动盒子位置。

节流阀：当上一个函数动画内容执行完毕，再去执行下一个函数动画，让事件无法连续触发

## 五、移动端网页特效

### 1.触屏事件

| 触屏touch事件 | 说明                          |
| ------------- | ----------------------------- |
| touchstart    | 手指触摸到一个DOM元素         |
| touchmove     | 手指在一个DOM元素上滑时触发   |
| touchend      | 手指在一个DOM元素上移开时触发 |

**触摸事件对象**（touchevent）

常见对象列表：

| 触摸列表       | 说明                                               |
| -------------- | -------------------------------------------------- |
| touches        | 正在触摸当前屏幕的所有手指的一个列表               |
| targetTouches  | 正在触摸当前DOM元素上的手指的一个列表              |
| changedTouches | 手指状态发生了改变的列表，从无到有，从有到无的变化 |

### 2.检测过渡完成事件：

transitionend 

### 3.classList

返回元素类名
添加类：element.classList.add('类名')
移除类:element.classList.remove('类名')
切换类:element.classList.toggle('类名')

**click延迟300ms解决方案**
原因是移动端双击屏幕会缩放页面

- 禁止缩放功能

  ```html
  <meta name="viewport" content="user-scalable=no">
  ```

* 利用touch事件自己封装这个事件解决300ms延迟
  1. 当我们手指触摸屏幕，记录当前触摸时间
  2. 当我们手指离开屏幕时，用离开时间减去触摸时间
  3. 如果小于150ms，并且没有滚动过屏幕，那么我们认为是点击事件

## 六、本地存储

特性：

1. 数据存储在用户浏览器
2. 设置、读取方便、甚至页面刷新不丢失数据
3. 容量较大，sessionStorage5M、localStorage约20M
4. 只能存储字符串，可以将对象JSON.stringify编码后存储

### 1.sessionStorage

1. 生命周期为关闭浏览器窗口
2. 在同一窗口下数据共享
3. 以键值对的形式存储

存储数据：sessionStorage.setItem(key,value)
获取数据：sessionStorage.getItem(key)
删除数据：sessionStorage.removeItem(key)
删除所有数据：sessionStorage.clear()  

### 2.localStorage

1. 生命周期永久生效，除非手动删除
2. 可以多窗口共享
3. 以键值对形式存储

存储数据：slocalStorage.setItem(key,value)
获取数据：localStorage.getItem(key)
删除数据：localStorage.removeItem(key)
删除所有数据：localStorage.clear()  

## 七、JQuery

### 1、JavaScript库

即library，是一个封装好的特定的集合（方法和函数）。从封装一大堆函数的角度理解库，就是在这个库中，封装了很多预先定义好的函数在里面，比如动画animate、hide、show。比如获取元素

常见的JavaScript库

* JQuery
* Prototype
* YUI
* Dojo
* Ext JS
* 移动端的zepto

注意：这些库都是对原生的JavaScript的封装，内部都使用JavaScript实现的
JavaScript封装了常用的功能代码、优化了DOM操作、事件处理、动画设计和Ajax交互
学习Jquery本质：就是学习调用这些函数

JQuery的优点：

* 轻量级
* 跨浏览器兼容
* 链式编程、隐式迭代
* 对事件、样式、动画支持，大大简化了DOM操作
* 支持插件扩展开发。
* 免费、开源

### 2.jQuery的入口函数

```js
//方法一
$(document).ready(function (){
	$('div').hide()//等着页面DOM加载完毕再去执行js代码
 })

//方法二
$(function () {
	$('div').hide()//等着页面DOM加载完毕再去执行js代码
})
```

1. 等着DOm结构渲染完毕即可执行内部代码，不必等到所有外部资源加载完成，jQuery帮我们完成了封装
2. 相当于原生js中的DOMContentLoaded
3. 不同于原生js中的load事件是等页面文档、外部的js文件、css文件、图片加载完毕才执行内部代码
4. 更推荐使用方法二。

### 3.jQuery的顶级对象$

1. $是jQuery的别称,在代码中可以使用jQuery代替$
2. $是jQuery的顶级对象，相当于原生JavaScript中的window。把元素利用$包装成jQuery对象，就可以调用jQuery的方法

### 4.DOM对象和jQuery对象

```js
//1.DOM对象    利用原生js获取的对象就是DOM对象
var MyDom = document.querySelector('div')
console.dir(MyDom)
//2.jQuery对象  用jquery方式获取过来的对象就是jQuery对象。
//本质：通过$把Dom元素进行了包装
//jQuery对象本质是：利用$对DOM对象包装后产生的对象(伪数组形式存储)
console.dir($('div'))
//jQuery对象只能使用jQuery方法，DOM对象只能使用原生的js属性和方法
```

DOM对象与jQuery对象之间是可以相互转换的

```js
//jQuery中没有play这个方法
// 1. DOM对象转换为 jQuery对象
let myVideo = document.querySelector('video');
$('myVideo')
// 2.  jQuery对象转换为DOM对象
$('video')[0]
$('video').get(0)
```

### 5.常用API

#### 1.jQuery选择器

1. 基础选择器

   ```js
   $('选择器') //里面选择器直接写CSS选择器即可，但是需要加引号
   ```

| 名称       | 用法            | 描述                     |
| ---------- | --------------- | ------------------------ |
| ID选择器   | $('#id')        | 获取指定ID的元素         |
| 全选选择器 | $('*')          | 匹配所有元素             |
| 类选择器   | $('.class')     | 获取同一类class的元素    |
| 标签选择器 | $('div')        | 获取同一类标签的所有元素 |
| 并集选择器 | $('div,p,li')   | 选择多个元素             |
| 交集选择器 | $('li.current') | 交集元素                 |

2. 层级选择器

| 名称       | 用法       | 描述                                                         |
| ---------- | ---------- | ------------------------------------------------------------ |
| 子代选择器 | $('ul>li') | 使用>,获取亲额儿子层级的元素；注意，并不会获取孙子层级的元素 |
| 后代选择器 | $('ul li') | 使用空格，代表后代选择器，获取ul下的所有li元素，包括孙子等   |

#### 2.隐式迭代

遍历内部DOM元素（伪数组形式存储）的过程就叫**隐式迭代**

#### 3.筛选选择器

| 语法       | 用法          | 描述                                     |
| ---------- | ------------- | ---------------------------------------- |
| :first     | $('li:first') | 获取第一个li元素                         |
| :last      | $('li:last')  | 获取最后一个li元素                       |
| :eq(index) | $('li:eq(2)') | 获取到的li元素中，选择索引号为2的元素    |
| :odd       | $('li:odd')   | 获取到的li元素中，选择索引号为奇数的元素 |
| :even      | $('li:even')  | 获取到的li元素中，选择索引号为偶数的元素 |

#### 4.jQuery筛选方法

| 语法                | 用法                           | 说明                                               |
| ------------------- | ------------------------------ | -------------------------------------------------- |
| parent()            | $('li').parent();              | 查找父级                                           |
| childrent(selector) | $('ul').children('li');        | 相当于$('ul>li'),最近一级(亲儿子)                  |
| find(selector)      | $('ul').find('li');            | 相当于$('ul li'),后代选择器                        |
| siblings(selector)  | $('.first').siblings('li');    | 查找兄弟节点，不包括自己本身                       |
| nextAll([expr])     | $('.first').nextAll()          | 查找当前元素之后所有的同辈元素                     |
| prevtAll([expr])    | $('.last').prevtAll()          | 查找当前元素之前所有的同辈元素                     |
| hasClass(class)     | $('div').hasClass('protected') | 检查当前元素是否包含某个特定的类，如果有则返回true |
| eq(index)           | $('li').eq(2)                  | 相当于$('li:eq(2)')                                |

#### 5.jQuery操作样式

**一、修改CSS**

1. 参数只写属性名，则返回属性值

   $(this).css("color")

2. 参数是属性名，属性值，逗号分割，是设置一组样式，属性必须加引号，值如果是数字可以不用跟单位和引号

   $(this).css("color","red")

3. 参数可以是对象形式，方便设置多组样式。属性名和属性值用冒号隔开，属性可以不用加引号,若是复合属性，则不加引号应该为驼峰命名法

   $(this).css("color":"white","font-size":"20px")

**二、设置类样式**

作用等同于之前的classList,可以操作类样式，注意操作类里面的参数不要加点

1. 添加类

   $("div").addClass("current")

2. 删除类

   $("div").remove("current")

3. 切换类

   $("div").toggleClass("current")

#### 6.jQuery效果

**显示隐藏**：show、hide、toggle（若显示则隐藏，否则反之）
显示语法规范：show([speed,[easing],[fn]])
参数：都可省略
1.speed：三种预定速度之一的字符串（slow、normal、fast）或表示动画时长的毫秒数
2.easing：用来指定切换效果，默认swing，可用参数linear
3.fn：回调函数，在动画完成之后执行

**滑动**：slideDown、slideUp、slideToggle
参数和上面一样

**淡入淡出**：fadeln、fadeOut、fadeToggle、fadeTo
前三个方法与前面一致，最后一个多了一个属性值
显示语法规范：**fadeTo**([[speed],opacity,[easing],[fn]])
参数：都可省略
1.speed：三种预定速度之一的字符串（slow、normal、fast）或表示动画时长的毫秒数
2.opacity：透明度必须写，取值0~1
3.easing：用来指定切换效果，默认swing，可用参数linear
4.fn：回调函数，在动画完成之后执行

**自定义动画**：animate
语法：animate(params，[speed]，[easing]，[fn])
参数：

1. params：想要更改的样式属性，以对象形式传递，必须写。属性名可以不带引号，如果是复合属性则需采用驼峰命名法。其余参数都可以省略
2. 后面三个属性与上面一致

事件切换：hover
hover([over],out)

1. over：鼠标移动到元素上时触发
2. out：鼠标移除元素时触发函数

**动画队列及停止排队方法**

1. 动画或效果队列

   动画或者效果一旦触发就会执行，如果多次触发，就造成多个页面或者效果排队执行

2. 停止排队
   stop()
   * stop方法用于停止动画或效果
   * 注意：stop()写到动画或者效果的前面，相当于停止上一次的动画
     例如：stop().slideDown()
