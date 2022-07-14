# webAPI的基本学习

- 作用：使用JS操作html和浏览器
- 分类：DOM（文档对象模型）、BOM（浏览器对象模型）

 <img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220626113415737.png" alt="image-20220626113415737" style="zoom:80%;" />

### DOM的内容

- DOM（Document Object Model——文档对象模型）是用来呈现以及与任意 HTML 或 XML文档交互的API
- 简单来说：DOM是浏览器提供的一套专门用来 操作网页内容 的功能
- 作用：开发网页内容特效和实现用户交互

### DOM树

- 内容：将HTML以树状的内容直观显示出来，也称文档树

- 作用：直观体现出标签与标签的关系

- ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
  </head>
  <body>
      文本
      <a href="">链接</a>
      <h1 class="" id=""></h1>
  </body>
  </html>
  ```

  <img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/0d429a429c4b10f6ba024de35a73da88b39e4b6e76b0f7bd95697db1ceaab0b5.gif" alt="0d429a429c4b10f6ba024de35a73da88b39e4b6e76b0f7bd95697db1ceaab0b5" style="zoom:200%;" />



### 获取DOM元素

- CSS选择器 	匹配到第一个元素，返回一个HTMLElement对象

  ```javascript
  //语法
  document.querySelector('CSS选择器')
  ```

- 匹配多个选择器，返回NodeList对象集合，得到是一个伪数组

  ```javascript
  document.querySelectorAll('CSS选择器')
  ```

- 其他方法

  ```javascript
  document.getElementByid('id名')
  document.getElementByTagName('标签名')
  document.getElementByClassName('类名')
  ```

  

### 设置和修改DOM元素

- 修改标签文本内容

  ```javascript
  //语法：
  元素.innerText='' 
  //只能识别内容，不能解释标签
  //可以解析标签 即：
  元素.innerHTML='<h3>会对html标签进行解析</h3>' 
  ```

  

### 设置与修改DOM元素的属性

- 语法：`对象.属性=值`，最常见的属性比如： **href**、**title**、**src** 等

  ```javascript
  //例子
  let pic =document.querySelector('img')
  pic.src='./images/pic2.jpg'
  ```

  

- 通过**style**修改CSS属性 

  ```javascript
  let box =document.querySelector('div')
  box.style.width='300px'
  box.style.paddingLeft ='300px'
  //注：有链接-符号的需要转换为小驼峰命名法
  //即：padding-left-->paddingLeft
  ```

- 修改标签类名

  ```javascript
  元素.clssName='新类名'
  //注：直接使用 className 赋值会覆盖以前的类名
  //保留可写
  元素.clssName='旧类名 新类名'
  ```

- 通过**clssList**操作css类名

  ```javascript
  //增加一个类名
  元素.classList.add('类名')
  //删除一个类
  元素.classList.remove('类名')
  //切换一个类,存在就删除,不存在就增加
  元素.classList.toggle('类名')
  ```

  

### 修改表单属性

- 作用：表单很多情况，也需要修改属性，比如点击眼睛，可以看到密码，本质是把表单类型转换为文本框

- 获取：DOM对象.属性名；设置：DOM对象.属性名=新值

  ```javascript
  表单.value='用户名'
  表单.type='password'
  ```

- 表单属性中添加就有效果,移除就没有效果,一律使用布尔值表示 如果为true 代表添加了该属性 如果是false 代表移除了该属性
  比如： disabled、checked、selected

### 定时器-**setInterval()** 间歇函数

- 开启定时器

  ```javascript
  setInterval(函数，间隔时间) //时间也毫秒为单位，1秒==1000ms
  ```

- 关闭定时器

  ```javascript
  let timer =setInterval(函数，间隔时间)
  clearInterval(timer)
  ```

  

----



### 事件

> 事件是在编程时系统内发生的动作或者发生的事情，比如用户在网页上单击一个按钮

#### 事件监听

>让程序检测是否有事件产生，一旦有事件触发，就立即调用一个函数做出响应，也称为 注册事件

语法：`元素.addEventListener('事件',要执行的函数)`

```javascript
//获取元素
let btn=document.querySelector('button')
//事件监听
btn.addEventListener('click',function(){
    alert('被点击了')
})
```



事件监听三要素：

- 事件源：那个dom元素被事件触发了，要获取dom元素
- 事件：有什么方式触发，比如鼠标点击**click**
- 事件触发时调用的函数

#### 版本

- DOM L0

  语法：`事件源.on事件=function(){}`

  ```javascript
  btn.onclick=function(){
     alert('点击')
  }
  ```

  

- DOM L2  :star:

  语法：`事件源.addEventlistener(事件，事件处理函数)`

  ```javascript
  btn.addEventListener('click',function(){
      alert('点击')
  })
  ```

  

#### 事件类型



#### ![image-20220702092821996](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220702092821996.png)

 

---



### 高阶函数

> 高阶函数可以被简单理解为函数的高级应用，JavaScript 中函数可以被当成【值】来对待，基于这个特性实现函数的高级应用



#### 函数表达式

```javascript
let counter=function(x,y){
    return x+y
}
//调用
let result=counter(1,2)
```

#### 回调函数

> 如果将函数A当作参数传递给函数B时，我们称函数A为回调函数
>
> 回调函数本质还是函数，只不过把它当成参数使用

使用场景

- 定时器**setInterval()** 间歇函数

  ```javascript
  function fn(){
      alert('我是回调函数')
  }
  //fn传递了给setInterval ，fn就是回调函数
  setInterval(fn,1000)
  ```

- 事件监听

  ```javascript
  btn.addEventListener('click',function(){
       alert('我是回调函数')
  })
  ```

----



### 环境变量

> 环境对象指的是函数内部特殊的变量 this ，它代表着当前函数运行时所处的环境
> 作用：弄清楚this的指向，可以让我们代码更简洁

- 函数的调用方式不同，this 指代的对象也不同
- 【谁调用， this 就是谁】 是判断 this 指向的粗略规则
-  直接调用函数，其实相当于是 window.函数，所以 this 指代 window

----



### 编程思想

#### 排他思想

当前元素为A状态,其他元素为B状态

使用：
1. 干掉所有人
使用for循环
2. 复活他自己
通过this或者下标找到自己或者对应的元素

```javascript
 //给点击的li加上pink类
	<li class='pink'>第一个</li>
    <li>第二个</li>
    <li>第三个</li>
  	 let lis = document.querySelectorAll('li')
    for (let i = 0; i < lis.length; i++) {
            lis[i].addEventListener('click', function () {
              // 干掉所有人
               for (let j = 0; j < btns.length; j++) {
                  btns[j].classList.remove('pink')
               }
                //复活自己
                 this.classList.add('pink')
                //==================分割线===========================
                //高级做法
                // 我只需要找出那个唯一的 pink类，删除
                document.querySelector('.pink').classList.remove('pink')
                // 我的
                this.classList.add('pink')
            })
        }
```



---



### DOM结点

> DOM树里每一个内容都称之为节点

结点类型

![image-20220702101440879](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220702101440879.png)

- 元素结点 :star:

  所有的标签：比如 `body` `div`，`html`是根节点

- 属性结点

  所有的属性，比如 `herf`

- 文本结点

  所有的文本

  

#### 结点的查找

结点的关系：父节点，子节点，兄弟节点

- 父节点的查找

  使用`parentNode`属性，返回最近一级的父节点，找不到返回**null**

  语法：`子元素.parentNode`

- 子结点的查找

  `childNodes` - 获得所有的子节点，包括文本节点（空格、换行）、注释节点等

  `chilrden` :star:  -获得所有元素节点，返回的还是一个伪数组

- 兄弟结点的查找

  `nextElementSibling`  查找下一个兄弟结点

  `previousElementSibling`  查找上一个兄弟节点

#### 结点的增加

>一般情况下，我们新增节点，按照如下操作
>
>1创建一个新的节点
>
>2把创建的新的节点放入到指定的元素内部

- 创建结点

  ```javascript
  documnet.createElement('标签名')
  ```

- 追加结点

  ```javascript
  //插入父元素的最后
  父元素.appendChild(要插入的元素)
  //插到某个子元素的前面
  父元素.insertBefore(要插入的元素,在哪个元素的前面)
  ```

  

#### 结点的克隆

>cloneNode会克隆出一个跟原标签一样的元素，括号内传入布尔值
>若为true，则代表克隆时会包含后代节点一起克隆
>若为false，则代表克隆时不包含后代节点
>默认为false

**语法**：`元素.cloneNode(布尔值)`

#### 结点的删除

>删除节点和隐藏节点（display:none） 有区别的： 隐藏节点还是存在的，但是删除，则从html中删除节点在 JavaScript 原生DOM操作中，要删除元素必须通过父元素删除

**语法**：`父元素.removeChild(要删除的元素)`

------



###  重绘和回流

浏览器进行界面渲染

<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220702104807814.png" alt="image-20220702104807814" style="zoom:150%;" />

- 解析（Parser）HTML，生成DOM树(DOM Tree)
- 同时解析（Parser） CSS，生成样式规则 (Style Rules)
- 根据DOM树和样式规则，生成渲染树(Render Tree)
- 进行布局 Layout(回流/重排):根据生成的渲染树，得到节点的几何信息（位置，大小）
- 进行绘制 Painting(重绘): 根据计算和获取的信息进行整个页面的绘制
- Display: 展示在页面上

#### 回流(重排)

>当 Render Tree 中部分或者全部元素的尺寸、结构、布局等发生改变时，浏览器就会重新渲染部分或全部文档的过程称为回流，简单理解影响到布局了，就会有回流

会导致回流的操作

- 页面的首次刷新
- 浏览器的窗口大小发生改变
- 元素的大小或位置发生改变
- 改变字体的大小
- 内容的变化（如：input框的输入，图片的大小）
- 激活css伪类 （如：:hover）
- 脚本操作DOM（添加或者删除可见的DOM元素）

#### 重绘

>由于节点(元素)的样式的改变并不影响它在文档流中的位置和文档布局时(比如：color、background-color、
>outline等), 称为重绘

**注：**重绘不一定引起回流，而回流一定会引起重绘。

练习：

```javascript
let s = document.body.stlye
s.padding = '2px' //重排 + 重绘
s.border = '1px solid red' // 重排 + 重绘
s.color = 'red'//重绘
s.backgroundColor = '#666' //重绘
s.fontSize= "14px" // 重排 + 重绘
```



----

### 事件高级

#### 事件对象

> 内容：事件对象是个对象，这个对象里有事件触发时的相关信息
>
> 例如：鼠标点击事件中，事件对象就存了鼠标点在哪个位置等信息

获取方法：

- 在事件绑定的回调函数的第一个参数就是事件对象

- 一般命名为 even 、ev 、e

  ```javascript
  元素.addEventListener('click',function(e){
      //e就是事件对象
  })
  ```

  

常用事件对象的属性

- `type` ：获取当前事件类型
- `clientX` / `clientY` ：获得光标相对于浏览器可见窗口左上角的位置
- `offsetX` / `offsetY` :   获取光标相对于当前DOM元素左上角的位置
- `key` ：用户按下的键盘的值，现在不提倡用 **keyCode**

#### 事件流

> 事件流指的是事件完整执行过程的流动路径，两个阶段：事件捕获和事件冒泡



<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220703184458601.png" style="zoom: 200%;" />

- 说明：假设页面里有个div，当触发事件时，会经历两个阶段，分别是捕获阶段、冒泡阶段

- 简单来说：捕获阶段是 从父到子 冒泡阶段是从子到父

**事件冒泡**

>   当一个元素的事件被触发时，同样的事件将会在该元素的所有祖先元素中依次被触发
>
>   简单理解：当一个元素触发事件后，会依次向上调用所有父级元素的同名事件
>
>   事件冒泡是默认存在的

**事件捕获**

>从DOM的根元素开始去执行对应的事件 (从外到里)

说明：

- addEventListener第三个参数传入true代表是捕获阶段触发（很少使用）
- 若传入false代表冒泡阶段触发，默认就是false
- 若是用 L0 事件监听，则只有冒泡阶段，没有捕获

**阻止事件流动**

- 因为默认就有冒泡模式的存在，所以容易导致事件影响到父级元素
- 若想把事件就限制在当前元素内，就需要阻止事件流动
- 阻止事件流动需要拿到事件对象
- 语法：`事件对象.stopProagation()`
- 此方法可以阻断事件流动传播，不光在冒泡阶段有效，捕获阶段也有效

**鼠标经过事件**：

- `mouseover `和 `mouseout` 会有冒泡效果

- `mouseenter` 和 `mouseleave`  没有冒泡效果(推荐)

**两种注册事件的区别：**

- 传统on注册（L0）
  - 同一个对象,后面注册的事件会覆盖前面注册(同一个事件)
  - 直接使用null覆盖偶就可以实现事件的解绑
  - 都是冒泡阶段执行的

- 事件监听注册（L2）

  - 语法: addEventListener(事件类型, 事件处理函数, 是否使用捕获)

  - 后面注册的事件不会覆盖前面注册的事件(同一个事件)
  - 可以通过第三个参数去确定是在冒泡或者捕获阶段执行
  - 必须使用removeEventListener(事件类型, 事件处理函数, 获取捕获或者冒泡阶段)
  - 匿名函数无法被解绑

#### 事件委托

> 事件委托其实是利用事件冒泡的特点， 给父元素添加事件，子元素可以触发

- **优点：**给父级元素加事件（可以提高性能）

- **实现：**`事件对象.target `可以获得真正触发事件的元素

---

### 滚动事件

>  作用：很多网页需要检测用户把页面滚动到某个区域后做一些处理， 比如固定导航栏，比如返回顶部

**事件名** `scroll`

```javascript
//可以给window或document添加滚动事件来监听整个页面
window.addEventListener('scroll',function(){
    //要执行的操作
})
```

### 加载事件 

####  load 事件

- 加载外部资源（如图片、外联CSS和JavaScript等）加载完毕时触发的事件
- 为什么要学？
  - 有些时候需要等页面资源全部处理完了做一些事情
  - 老代码喜欢把  script  写在  head  中，这时候直接找  dom  元素找不到

-  事件名：`load`

-  监听页面所有资源加载完毕：

  - 给 window 添加 load 事件

    ```javascript
    window.addEventListener('load',function(){
        //要执行的操作
    })
    ```

-  注意：不光可以监听整个页面资源加载完毕，也可以针对某个资源绑定load事件

#### DOMContentLoaded

- 当初始的 HTML 文档被完全加载和解析完成之后，DOMContentLoaded 事件被触发，而**无**需等待样式表全加载

- 事件名：`DOMContentLoaded`

-  监听页面DOM加载完毕：

  -  给 document 添加 DOMContentLoaded 事件

    ```javascript
    document.addEventListener('DOMContentLoaded',function(){
        //要执行的操作
    })
    ```

    

---

### 元素大小和位置

**三大家族**

- scroll家族
- offest家族
- client家族

#### scroll家族

> 作用：检测页面滚动的距离

<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220710212619434.png" alt="image-20220710212619434" style="zoom:200%;" />

- 获取宽高

  -  获取元素的**内容总宽高（不包含滚动条）**返回值不带单位
  -  scrollWidth 和 scrollHeight

- 获取位置（属性可修改）

  - 获取元素内容往左、往上滚出去看不到的距离
  -  scrollLeft和scrollTop

  ```javascript
  div.addEventListener('scroll',function(){
      console.log(this.scrollTop)
  })
  ```

  注：`document.documentElement` ：HTML 文档返回对象为HTML元素



#### offest家族

![image-20220710213109240](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220710213109240.png)

- 获取宽高
  -  获取元素的自身宽高、包含元素自身设置的宽高、padding、border
  -  offsetWidth 和 offsetHeight
- 获取位置（只读，不可修改）
  - 获取元素距离自己定位父级元素的左、上距离

####  client家族

<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220710213252589.png" alt="image-20220710213252589" style="zoom:150%;" />

- 获取宽高
  - 获取元素的可见部分宽高（不包含边框，滚动条等）
  -  clientWidth和clientHeight
- 位置
  -  clientLeft和clientTop 注意是只读属性

`resize`事件

- 改变窗口大小的时候触发的事件，类似css3媒体查询

---

### Window对象

#### BOM

> 浏览器对象模型

<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220713111536299.png" alt="image-20220713111536299" style="zoom:200%;" />

- window 是浏览器内置的全局对象，我们所学习的 web apis 的知识内容都是基于 window 对象实现的

- window 对象下包含了 `navigator` 、`location` 、`doucment`   `history` 、 `srceen` 5个属性，即 BOM

- document 是实现 DOM 的基础，它其实是依附于 window 的属性

- 依附于 window 对象的所有属性和方法，使用时可以省略 window

  

#### 定时器-延时函数

>  JavaScript 内置的一个用来让代码延迟执行的函数，叫 setTimeout

语法：`setTimeout(回调函数,等待的毫秒数)`

**setTimeout** 仅执行一次，简单来说把一段代码延迟执行

清除延时函数语法 ：`clearTimeout(延时函数的id)`

结合函数的递归可以实现 setInterval 间歇函数 一样的功能

```javascript
function myInterval(){
    let d=new date();
    //写入页面
    clock.innertext=d.toLocaleString();
    //调用自己 一直循环，倒计时效果
    setTimeout(myInterval,1000);  
}
myInterval();
```



#### JS执行机制 （面试）:star:

>JavaScript 语言的一大特点就是单线程，也就是说，同一个时间只能做一件事。。这是因为 Javascript 这
>门脚本语言诞生的使命所致——JavaScript 是为处理页面中用户的交互，以及操作 DOM 而诞生的。比
>如我们对某个 DOM 元素进行添加和删除操作，不能同时进行。 应该先进行添加，之后再删除。

> 单线程就意味着，所有任务需要排队，前一个任务结束，才会执行后一个任务。这样所导致的问
> 题是： 如果 JS 执行的时间过长，这样就会造成页面的渲染不连贯，导致页面渲染加载阻塞的感觉。

同步和异步

>为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许
>JavaScript 脚本创建多个线程。于是，JS 中出现了同步和异步。

- 同步

  - 前一个任务执行完才执行后一个任务，程序执行的顺序和代码排列顺序一样

- 异步

  - 执行一个某个任务费很长时间，在做这个任务的同时，还可以去处理其他的任务

    比如：做饭时，等水开的期间可以去其他事，比如切菜

- 他们的本质区别： 这条流水线上各个流程的执行顺序不同。

---



- 同步任务

  - 同步任务都在主线程上执行，形成一个执行栈。

- 异步任务

  - JS 的异步是通过回调函数实现的

  - 一般来说异步任务有以下三种类型

    1、普通事件，如 click、resize 等
    2、资源加载，如 load、error 等
    3、定时器，包括 setInterval、setTimeout 等

  - 异步任务相关会添加的任务队列（消息队列）中

---

**执行机制**

1. 先执行执行栈里面的同步任务
2. 异步任务放在消息队列中
3. 一旦执行栈的执行任务完毕，系统会依次读取消息队列里的异步任务，被读取的异步任务
   结束等待状态，进入执行栈，开始执行

<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220713115651765.png" alt="image-20220713115651765" style="zoom:150%;" />

**事件循环**（event loop）

> 由于主线程不断的重复获得任务、执行任务、再获取任务、再执行，所以这种机制被称为事件循环（ event loop）



![image-20220713115913074](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220713115913074.png)

----

#### location对象

> location 的数据类型是对象，它拆分并保存了 URL 地址的各个组成部分

 **常用属性和方法：**

-  href 属性获取完整的 URL 地址，对其赋值时用于地址的跳转
-  search 属性获取地址中携带的参数，符号 ？后面部分
-  hash 属性获取地址中的啥希值，符号 # 后面部分
-  reload 方法用来刷新当前页面，传入参数 true 时表示强制刷新

语法：`loaction.属性`  `loactiom.方法()`



#### navigator对象

> navigator的数据类型是对象，该对象下记录了浏览器自身的相关信息

 常用属性和方法： 通过 userAgent 检测浏览器的版本及平台

```java
// 检测 userAgent（浏览器信息）
!(function () {
const userAgent = navigator.userAgent
// 验证是否为Android或iPhone
const android = userAgent.match(/(Android);?[\s\/]+([\d.]+)?/)
const iphone = userAgent.match(/(iPhone\sOS)\s([\d_]+)/)
// 如果是Android或iPhone，则跳转至移动站点
if (android || iphone) {
location.href = 'http://m.itcast.cn'
}
})()
```



####  histroy对象

> history 的数据类型是对象，该对象与浏览器地址栏的操作相对应，如前进、后退、历史记录等



| history对象和方法 | 作用                                    |
| ----------------- | --------------------------------------- |
| back()            | 可以后退功能                            |
| forward()         | 可以前进功能                            |
| go(参数)          | 前进，后退功能，参数决定，-1后退，1前进 |



#### 本地存储

>随着互联网的快速发展，基于网页的应用越来越普遍，同时也变的越来越复杂，为了满足各种各样的需求，会经常性在
>本地存储大量的数据，HTML5规范提出了相关解决方案

1. 数据存储在用户浏览器中
2. 设置、读取方便、甚至页面刷新不丢失数据
3. 容量较大，sessionStorage和localStorage约 5M 左右

**localStorage**

1. 生命周期永久生效，除非手动删除 否则关闭页面也会存在
2. 可以多窗口（页面）共享（同一浏览器可以共享）
3. 以键值对的形式存储使用

语法

- 存储数据：`localStorage.setItem(key, value)`
- 获取数据：`localStorage.getItem(key)`
- 删除数据：`localStorage.removeItem(key)`

存储复杂数据类型存储：

> 本地只能存储字符串,无法存储复杂数据类型.需要将复杂数据类型转换成JSON字符串,在存储到本地

**JSON.stringify(复杂数据类型) ：**

将复杂数据转换成JSON字符串 **存储** 本地存储中

**JSON.parse(JSON字符串)：**

将JSON字符串转换成对象 **取出** 时候使用

---

sessionStorage（了解）
 	1. 生命周期为关闭浏览器窗口
 	2. 在同一个窗口(页面)下数据可以共享
 	3. 以键值对的形式存储使用
	4. 用法跟localStorage 基本相同

#### 自定义属性

固有属性：

> 标签天生自带的属性 比如class id title等, 可以直接使用点语法操作

自定义属性:

> 由程序员自己添加的属性,在DOM对象中找不到, 无法使用点语法操作,必须使用专门的API

- 获取自定义属性 ：`getAttribute('属性名')`
- 设置自定义属性：`setAttribute('属性名', '属性值')`
-  删除自定义属性：`removeAttribute('属性名') `

data-自定义属性：

> 传统的自定义属性没有专门的定义规则,开发者随意定值,不够规范,所以在html5中推出来了专门的data-自定义属性 在标签上一律以data-开头

在DOM对象上一律以dataset对象方式获取

![image-20220713122248633](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220713122248633.png)

---



### 正则表达式

> 正则表达式（Regular Expression）是用于匹配字符串中字符组合的模式。在 JavaScript中，正则表达式也是对象

正则表达式在 JavaScript中的使用场景：

- 例如验证表单：用户名表单只能输入英文字母、数字或者下划线， 昵称输入框中可以输入中文(匹配)
- 比如用户名: ` /^[a-z0-9_-]{3,16}$/`
- 过滤掉页面内容中的一些敏感词(替换)，或从字符串中获取我们想要的特定部分(提取)等 。



#### 语法

**使用**：

1. 定义规则
2. 查找

**语法**：`let 变量名=/表达式/`

- / / 是正则表达式字面量，比如 ：`let reg=/abc/`

**判断**：

- test() 方法 用来查看正则表达式与指定的字符串是否匹配 ，返回 false 或 true

  ```javascript
  let str = 'hello ,world'
  let reg = /hello/
  console.log(reg.test(str))  //true
  ```

- exec() 方法 在一个指定字符串中执行一个搜索匹配

  如果匹配成功，exec() 方法返回一个数组，否则返回null

#### 元字符

> 是一些具有特殊含义的字符，可以极大提高了灵活性和强大的匹配功能。

- 比如，规定用户只能输入英文26个英文字母，普通字符的话 abcdefghijklm…..

  但是换成元字符写法： [a-z]



**方便记忆和学习，众多的元字符进行了分类：**

1. **边界符**（表示位置，开头和结尾，必须用什么开头，用什么结尾）

   正则表达式中的边界符（位置符）用来提示字符所处的位置，主要有两个字符

   ![image-20220714135805923](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220714135805923.png)

   **注意**：如果 `^` 和 `$`在一起，表示必须是精确匹配。

2. **量词** （表示重复次数）

   量词用来 设定某个模式出现的次数

   ![image-20220714135915669](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220714135915669.png)

   **注意**： 逗号左右两侧千万不要出现空格

3. **字符类** （比如  `\d`  表示 0~9）

   - [ ] `-` 连字符

     使用连字符 `-` 表示一个范围

   - [ ] 比如：

     1. [a-z] 表示 a 到 z 26个英文字母都可以
     2.  [a-zA-Z] 表示大小写都可以
     3.  [0-9] 表示 0~9 的数字都可以

   - [ ]  [ ] 里面加上 `^` 取反符号
     比如：
     `[^a-z] `匹配除了小写字母以外的字符
       注意要写到中括号里面

   - [ ]  `. `  匹配除换行符之外的任何单个字符

   - [ ]  预定义：指的是某些常见模式的简写方式

   ![image-20220714140426304](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220714140426304.png)

4. **修饰符**

   修饰符约束正则执行的某些细节行为，如是否区分大小写、是否支持多行匹配等

   语法：

   `/表达式/修饰符`

    i  是单词 ignore 的缩写，正则匹配时字母不区分大小写
   g  是单词 global 的缩写，匹配所有满足正则表达式的结果

   ```javascript
   console.log(/a/i.test('a'))  //true
   console.log(/a/i.test('A'))  //true
   ```

   替换 replace 替换：（过滤敏感词）

   ```javascript
   字符串.replace(/正则表达式/，'替换的文本')
   ```

   

 


​	
