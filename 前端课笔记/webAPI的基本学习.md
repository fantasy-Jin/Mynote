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