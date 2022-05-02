# HTML标签

整体结构

```html
<html> <!--开始标签-->
<html>
	<head>
		<meta charset="utf-8" />  <!--字符编码避免网页文字乱码-->
		<title>网页的标题</title>
	</head>
	<body>
	<!--网页的基本内容-->
	</body>
</html> <!--结束标签-->

```

## 初级标签

1. 标题标签

   > H1，H2，....，H6。（1-->6）大标题-->小标题，成对出现，开始标签 `<H1>`，一个结束标签 `</H1>`。

2. 段落标题

   >段落是通过 `<p> `标签进行定义的，成对出现，开始标签`` <p>``，一个结束标签 `</p>`。

3. 文字标签

   > `<strong></strong>`，加粗文字标签；`<em></em>`斜体文字标签，可嵌套

4. 符号标签

   >`<del></del>`，在文字上添加删除线，如：~~文字~~

## 高级标签

1. 块状标签

   >`<div></div>`,每一个div占满一整行。  `<span></span>`，文本信息在一行展示

2. 空格和换行，尖括号

   >`<br>` 换行标签，`&nbsp;`空格符号，`&lt`左尖括号，`&gt;`右尖括号

 3. 有序列表标签

    > ```html
    > <ol>			  <!--网页显示-->
    >   <li>第一条</li>	<!--1.第一-->
    >   <li>第二条</li>	<!--2.第二-->
    >   <li>第三条</li>	<!--3.第三-->
    > </ol>
    > ```
    >
    >  `<ol>`可以增加属性，type，换排序符号；
    >
    > 如`<ol type="A">`，就从A，B顺序排列；符号可以换`A,a,1,i I`，不填默认数值`1`；
    >
    > 倒叙`<ol reversed="reversed">`；
    >
    >  `<ol start="数值">`，更换开始符号的数值；

4. 无序列表标签

   >```html
   ><ul>			  
   >  <li>第一条</li>	
   >  <li>第二条</li>	
   >  <li>第三条</li>	
   ></ul>
   >```
   >
   >默认每一段文本前面显示小圆点
   >
   >属性：`<ul type=disc>`默认值实心小圆点，`circle`空心小圆点，`square`小方块

  5. 图片插入

     > `<img src="图片路径">`
     >
     > 包括：
     >
     > 1，网上url；
     >
     > 2，本地的绝对路径(同一个文件夹下，直接写图片文件名)；
     >
     > 3，本地的相对路径(不同一个文件夹下，写完整图片路径)；
     >
     > 属性：
     >
     > 1，`<img src="图片路径" alt="图片占位符">`，即图没有加载出来时显示
     >
     > 2，`<img src="图片路径" title=”图片提示符“>`，即鼠标移到图时显示

6. 链接标签a

     >1. 超链接：`<a href="网址">网站名</a>`
     >2. 锚点：`<a href="#id">文字</a>`；id指某个标签的id名字，运用于：页面目录，回到顶部
     >3. 打电话或发邮件：`<a href="tel:电话号码">文字</a>`；`<a href="mailto:邮箱地址">文字</a>`
     >4. 协议限定符：使用js
     >
     >属性：`target=_blank`点击链接在新页面弹出

7. 表单

   > 信息输入框
   >
   > ```html
   > <form method="get" action="" > 	<!--action：发送出去的地址-->
   >  	name: <input type="text" name="name" />		 <!--文本输入框，name：数值内容-->
   > 	password: <input type="password" name="password" />	<!--密码输入框，name：数值内容-->
   >   <input type="submit" value="Submit" />  			<!--提交按键，value：数据值-->
   > </form>
   > ```
   >
   > 单选框
   >
   > ```html
   > <form method="get" action="" > 	<!--action：发送出去的地址-->
   > 	<p> 选择其中一个 </p>
   >         1.第一个<input type="radio" name="name">
   >         1.第一个<input type="radio" name="name">
   >         1.第一个<input type="radio" name="name">
   >   <input type="submit" value="Submit" />  		<!--提交按键，value：数据值-->
   > </form>
   > ```
   >
   > 