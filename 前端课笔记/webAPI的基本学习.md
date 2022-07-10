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
  - 老代码喜欢把 script 写在 head 中，这时候直接找 dom 元素找不到

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
  -  scrollWidth和scrollHeight

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
  -  offsetWidth和offsetHeight
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
