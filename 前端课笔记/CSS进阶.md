# CSS进阶

## 利用绝对定位居中

```css
.conter{
    with:100px;
    higth:200px;
     /* 方法一 */
    position:absolute;
    left:50%;
    top:50%;
    margin-top: -100px;    /* ⾼度的⼀半 */
    margin-left: -50px;    /* 宽度的⼀半 *
    /* 方法二 */
    position:absolute;
    left:0; top:0; right:0; bottom:0;
   	margin:auto; /*实现绝对定位元素的居中(上下左右均0位置定位；margin: auto)*/
	/* 子绝父相的居中*/
    left:50%;
    top:50%;
    transform：translate(-50%，-50%); /* 让子盒子往左+往上走自己的一半 */
}
```

-----

## 伪元素

> 伪元素：不存在文档中，是虚拟的元素，是创建新元素。代表某个元素的子元素，这个子元素虽然在逻辑上存在，但却并不实际存在于文档树中

`::after和::beore`

```css
/*标签前面*/
.item::before {
content: ''; /* 内容 ，不需要可以空，但是必定写上*/
color: red		/* 和其他正常元素一样都可以定义其他属性*/
}
/*标签后面*/
.item::after {
content: '';
color: red
}
```

## margin塌陷，合并

### BFC

>块级格式化上下文，它是一个独立的渲染区域，让处于BFC内外的元素相互隔离，使内外元素的布局不会相互影响。
>
>触发方法：1. ` position:absolute;`	2. `disply:inline-block;`	3. `float:left/right;`	4. `overflow:hidden;`
>
>注意： ` position:absolute;`	`float:left/right;`	把内部元素转换成`inline-block`

### margin塌陷

<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220506133652940.png" alt="image-20220506133652940" style="zoom: 80%;" />

> - 父子关系的子元素里，让子元素距离父元素的顶部50px,如果直接只给子元素`margin-top：50px;`子元素并没有距离父元素顶部50px，而是让父元素距离顶部有了50px的距离，也就是父元素的顶棚对子元素来说`没有作用`，相当于塌陷下来了，这就是所谓的margin塌陷。
>
> - 解决方式
>
>   方案1： 子元素的margin-top改为padding-top
>   方案2：给父元素添加样式触发BFC

### margin合并

<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220506133627068.png" alt="image-20220506133627068" style="zoom:80%;" />

>- 两个兄弟元素，一个设置下边距为50px,一个设置上边距为30px；
>
>- 结果：两个元素之间的间距是50px,也就是它们的margin-top和margin-bottom合并了，显示的是较大值。
>
>- 解决方案
>
>  方案1：给其中一个兄弟元素套一个父元素，并且设置为overflow:hidden
>
>  方案2：只给其中一个元素margin-top或margin-bottom设置想要的间距

---

## CSS float 属性

float属性指定一个盒子（元素）是否应该浮动。

**注意：** 绝对定位的元素忽略float属性;

```css
div{
float:right;	/* 向右浮动 */
}
div{
float:left;		/* 向左浮动 */
}
```

浮动元素会产生浮动流

- 浮动流元素，块级元素（block）看不见，会覆盖浮动流元素
- 产生BFC的元素和文本类属性（inline）的元素看得到浮动元素，不会覆盖

解决方法

- 方法一

  给浮动的父级元素设置高度来占位，这样后面的元素就不会向上补齐。

- 方法二
  在浮动元素的后面添加一个元素，并添加一个`clear:both` 的属性来清除浮动

- 方法三

  利用 `overflow: hidden/auto`清除浮动。子元素可以撑开父级的高度

- 方法四

  利用伪元素清除浮动，给父级添加伪元素
  
  ```css
  .item::after {
  	content: '';
  	display: block;
    	clear:both;
  }
  ```
  
  

## CSS补充

- 单行文本超出容器截断文字用`...`省略

  ```css
  white-space: nowrap;	 /* 文本强制在一行上显示 */
  overflow: hidden;	/*对超出内容进行裁减 */
  text-overflow:ellipsis;	/* 	显示省略符号...来代表被修剪的文本*/
  ```

  

- 背景图片

  ```css
  div{
      background-image:url(图片路径);		/* 插入背景图片 */
      background-repeat:no-repeat;	/* 如果图片小，默认下，铺满容器，no-repeat取消重复 */
      background-position:center;		/* 图片位置 */
      /*
      图片位置可用值：
  	left top
      left top
      ....
      =====
      x% y%
      水平垂直位置
      */
  }
  ```
  
- 嵌套问题

  行级元素只能嵌套行级元素

  块级元素可以嵌套任何元素

  >特殊注意：
  >
  >`p`标签不能嵌套`div`标签
  >
  >`a`标签不能嵌套`a`标签

