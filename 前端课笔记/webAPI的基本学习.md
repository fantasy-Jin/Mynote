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

  
