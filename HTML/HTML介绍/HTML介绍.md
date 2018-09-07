# HTML介绍

## 目录结构

1. HTML入门
2. HEAD
3. HTML文字基础
4. 创建超链接
5. 文本排版
6. 文档与网站结构
7. HTML调试
8. 实践：信件
9. 实践：结构化页面

## 1 HTML入门

### 1.1 HTML

HTML (HyperText Markup Language) 不是一种编程语言;它是一种标记语言，用于告诉您的浏览器如何构造您访问的网页。

### 1.2 剖析HTML元素

[HTML元素](../TEST_PROJ/images/HTML_ELEMENT.png)

### 1.3 实践

[Em-Test.html](../TEST_PROJ/Em-Test.html)

### 块级元素和内联元素

块级元素在页面中以块的形式展现 —— 相对与其前面的内容它会出现在新的一行，其后的内容也会被挤到下一行展现。
内联元素通常出现在块级元素中并包裹文档内容的一小部分，而不是一整个段落或者一组内容。内联元素不会导致文本换行：它通常出现在一堆文字之间例如超链接元素<a>或者强调元素<em>和 <strong>。

### 空元素

不是所有元素都拥有开始标签，内容和结束标记. 一些元素只有一个标签，通常用来在此元素所在位置插入/嵌入一些东西 。例如：元素<img>。

### 为元素添加属性

<a href="https://www.mozilla.org/" title="The Mozilla homepage">favorite website</a>

### 布尔属性

他们只能有跟它的属性名一样的属性值。
<input type="text" disabled> 

### 为HTML添加特征

TIPS:
```
如果你的页面html文件是放在本地的，比如用浏览器打开桌面上的html文件，是可以访问本地图片文件的。
如果你的html是在web服务器上的，即浏览器的地址是http://xxx.xxx/xx.html而不是file:///C:/xxx.html，那么是不允许打开file://开头的本地图片的，这是出于安全考虑的。这种情况下你可以按F12看看浏览器的错误信息是不是“not allowed to load local resource”。
```
[实验代码](../TEST_PROJ/Em-Test.html)

### HTML中的空白

无论你用了多少空白(包括空白字符，包括换行), 当渲染这些代码的时候，HTML解释器会将连续出现的空白字符减少为一个单独的空格符。


### 特殊字符

|原意字符|等价字符引用|
|:-----:|:-----:|
| < | \&lt; |
| > | \&gt; |
| " | \&quot;|
| ' | \&apos;|
| & | \&amp;|

### HTML注释

```
<!-- -->
```
