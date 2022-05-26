# 淘宝网（静态）HTML+CSS 技术笔记要点

##  重置样式

- 写网页时，新建一个reset.css，用来重置HTML页面的样式，因为许多标签默认有padding和margin

## CSS@用法

```css
/* 
    @charset    设置样式表的编码
    @import     引入其他样式文件
    @media      媒体查询
    @font-face  自定义字体
*/
```

## 设置网页图标

```css
<link rel="icon" href="favicon.ico">
/* ico的图标的格式 其他格式需要转换成ico格式才可设置网页图标篇 */
```
效果图
![image-20220515100737000](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220515100737000.png)



网页的logo图片通常用H标签

## base标签的作用

一个单标签，位于网页头部文件的head标签内，一个页面最多只能使用一个base元素，用来提供一个指定的默认目标，也算是一种表达路径和连接网址的标记

###  **base target属性**

```css
/* 例如 */
<base target="_blank">
```

target属性是网页窗口的打开方式，在base标签中设置该属性，那么页面中所有的链接都将遵循这个方式来打开网页，分别有如下几种选择：

- `_blank` ：在新窗口打开链接页面

- `_parent`：在上一级窗口中打开链接。
- `_self` ： 在当前窗口打开链接,此为默认值，可以省略。
- `_top`： 在浏览器的整个窗口打开链接，忽略任何框架

## 引入字体图标

### 阿里巴巴矢量图标库

1. 选择想要的图标加入购物车
2. 然后进入购物车点击下载代码，解压
3. 项目目录下新建了个fonts目录来放`iconfont.ttf`文件
4. 在index.css通过@引入字体和css

## 怪异盒模型

```css
盒模型：
1）标准盒模型
    总宽度 = border(左右) + width + padding(左右)
    总高度 = border(上下) + height + padding(上下)
2）IE混杂模型（怪异盒模型  -->  box-sizing: border-box）
    总宽度 = width
    总高度 = height
```

## 以图换字

网速不够的时，浏览器就会采用默认的加载策略，也就是去掉网页的css和javaScript.但这时仍需保证网站的可用性，所以采用以图换字方法

1. 文字隐藏

   ```css
   /* 文字放span标签 设置display隐藏 */
   h1 {
   width: 66px;
   height: 66px;
   background: url(...);
   font-size: 12px;
   }
   span {
   display: none;
   }
   ```

2. 负缩进

   ```css
   h1 {
   width: 66px;
   height: 66px;
   background: url(...);
   font-size: 12px;
   text-indent:-9999px;
   }
   ```

3. 字体大小

   ```css
   h1 {
   width: 66px;
   height: 66px;
   background: url(...);
   font-size: 0;
   }
   ```

   

##  渐变颜色

线性渐变

语法

```css
background-image: linear-gradient(direction, color-stop1, color-stop2, ...);
/* 方向(可省略，默认：to bottom), 起始颜色, 结束颜色*/
```

 从上到下（默认情况下）

```css
 background-image: linear-gradient(#e66465, #9198e5);
```

效果图

<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220515103930539.png" alt="image-20220515103930539" style="zoom: 80%;" />

----

角度渐变

语法

```css
background-image: linear-gradient(angle, color-stop1, color-stop2);
/* 与上类似*/
```

实例

```css
background-image: linear-gradient(-90deg, red, yellow);
```

效果图![image-20220515110517025](https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220515110517025.png)



## 使 ul 列表元素居中对齐

- 当ul列表中的所有li元素需要在父级盒子内部居中显示时，不能用 float: left; 
- 直接在ul中设置"text-align: center;", 再将li元素的display设置为inline-block，就可以实现居中显示。

## 表格布局

- `table`标签

  ```css
  /* 表头为th；普通单元格为td；行为tr */
  <table border="1">
    <tr>
      <th>Month</th>
      <th>Savings</th>
    </tr>
    <tr>
      <td>January</td>
      <td>100</td>
    </tr>
    <tr>
      <td>February</td>
      <td>80</td>
    </tr>
  ```

  效果图：<img src="https://picgo-fantasy06.oss-cn-guangzhou.aliyuncs.com/img/image-20220515112224963.png" alt="image-20220515112224963" style="zoom:50%;" />

 -  淘宝实用

    ```css
    /* 边框模式---合并的模式：即两个单元格之间的的边框只需要显示一个就行 */
    table {
        border-collapse: collapse;  
    }
    th,td {
        padding: 0;
    }
    ```

## .webp（图片格式）

- .webp 是谷歌开发的一种图片格式，只能用于在网站中显示，其体积相较于普通的图片格式小得多，且图片的清晰度不变，目前   IE不支持、火狐在65以上的版本支持，谷歌支持。

## 词强制换行

```css
/* 在空格的地方强制换行 */
word-break: keep-all; 
```

