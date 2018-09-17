# CSS的值和单位

## 值

- 数值: 长度值，用于指定例如元素宽度、边框（border）宽度或字体大小；以及无单位整数。用于指定例如相对线宽或运行动画的次数。
- 百分比: 可以用于指定尺寸或长度——例如取决于父容器的长度或高度，或默认的字体大小。
- 颜色: 用于指定背景颜色，字体颜色等。
- 坐标位置: 例如，以屏幕的左上角为坐标原点定位元素的位置。
- 函数: 例如，用于指定背景图片或背景图片渐变

### 数值

像素 (px) 是一种绝对单位（absolute units）， 因为无论其他相关的设置怎么变化，像素指定的值是不会变化的。其他的绝对单位如下：

mm, cm, in: 毫米（Millimeters），厘米（centimeters），英寸（inches）
pt, pc: 点（Points (1/72 of an inch)）， 十二点活字（ picas (12 points.)）

也有相对单位，他们是相对于当前元素的字号（ font-size ）或者视口（viewport ）尺寸。

em:1em与当前元素的字体大小相同（更具体地说，一个大写字母M的宽度）。CSS样式被应用之前，浏览器给网页设置的默认基础字体大小是16像素，这意味着对一个元素来说1em的计算值默认为16像素。
但是要小心—em单位是会继承父元素的字体大小，所以如果在父元素上设置了不同的字体大小，em的像素值就会变得复杂。现在不要过于担心这个问题，我们将在后面的文章和模块中更详细地介绍继承和字体大小设置。em是Web开发中最常用的相对单位。

ex, ch: 分别是小写x的高度和数字0的宽度。这些并不像em那样被普遍使用或很好地被支持。

rem: REM（root em）和em以同样的方式工作，但它总是等于默认基础字体大小的尺寸；继承的字体大小将不起作用，所以这听起来像一个比em更好的选择，虽然在旧版本的IE上不被支持（查看关于跨浏览器支持 Debugging CSS.)

vw, vh: 分别是视口宽度的1/100和视口高度的1/100，其次，它不像rem那样被广泛支持。
使用相对单位是非常有用的-你可以相对于你的字体或视口大小来调整HTML元素的大小，这意味着，假设整个网站上的文本大小被视力障碍用户调整为原来的两倍，而网站的布局仍将保持正确。

### 无单位的值

```
margin: 0;

p {
  line-height: 1.5;
}
```

## 百分比
width: 650px; width: 75%;
这两种不同的框布局类型通常被称为动态（流体）布局（跟随浏览器视口大小的变化）和固定宽度布局（不管怎样都保持不变），两种布局方式有着不同的应用场景：

可以使用动态布局来确保标准文档始终适合于屏幕，并且可以在不同大小的移动设备屏幕上表现良好。
一个固定宽度的布局可以用来保持在线地图的大小相同；浏览器视口可以在地图上滚动，只在一个时间内查看一定数量的地图。您可以立即看到的量取决于您的视口有多大。

##　颜色

### 关键词

```
p {
  background-color: red;
}
```

### 16进制值

```
/* equivalent to the red keyword */
p:nth-child(1) {
  background-color: #ff0000;
}

/* equivalent to the blue keyword */
p:nth-child(2) {
  background-color: #0000ff;
}

/* has no exact keyword equivalent */
p:nth-child(3) {
  background-color: #e0b0ff;
}
```

### RGB

```
/* equivalent to the red keyword */
p:nth-child(1) {
  background-color: rgb(255,0,0);
}

/* equivalent to the blue keyword */
p:nth-child(2) {
  background-color: rgb(0,0,255);
}

/* has no exact keyword equivalent */
p:nth-child(3) {
  background-color: rgb(224,176,255);
}
```

### HSL

1. 色调：颜色的底色调。这个值在0到360之间，表示色轮的角度。
2. 饱和度：饱和度是多少？这需要一个从0-100%的值，其中0是没有颜色（它将显示为灰色），100%是全彩色饱和度。
3. 明度：颜色有多亮或明亮？这需要一个从0-100%的值，其中0是无光（它会出现全黑的），100%是充满光的（它会出现全白）。

```
/* equivalent to the red keyword */
p:nth-child(1) {
  background-color: hsl(0,100%,50%);
}

/* equivalent to the blue keyword */
p:nth-child(2) {
  background-color: hsl(240,100%,50%);
}

/* has no exact keyword equivalent */
p:nth-child(3) {
  background-color: hsl(276,100%,85%);
}
```

### RGBA和HSLA

RGB和HSL都有相应的模式——RGBA和HSLA——不仅允许您设置想要显示的颜色,还有此颜色的透明度（ transparency ）
它们和与之相应的函数采用同样的参数,再加上第四个范围在0-1的值——设置透明度,或者说alpha通道。0是完全透明的,1是完全不透明的。

```
p {
  height: 50px;
  width: 350px;
}

/* Transparent red */
p:nth-child(1) {
  background-color: rgba(255,0,0,0.5);
  position: relative;
  top: 30px;
  left: 50px;
}

/* Transparent blue */
p:nth-child(2) {
  background-color: hsla(240,100%,50%,0.5);
}
```

### 不透明度（Opacity）

```
/* Red with RGBA */
p:nth-child(1) {
  background-color: rgba(255,0,0,0.5);
}

/* Red with opacity */
p:nth-child(2) {
  background-color: rgb(255,0,0);
  opacity: 0.5;
}
```

### 函数

你在其他地方也会看到函数——每当你看到一个名字后跟着括号,括号里包含用逗号分隔的一个或多个值,那么你所使用的就是一个函数。例如:

```
/* calculate the new position of an element after it has been rotated by 45 degress */
transform: rotate(45deg);
/* calculate the new position of an element after it has been moved across 50px and down 60px */
transform: translate(50px, 60px);
/* calculate the computed value of 90% of the current width minus 15px */
width: calc(90%-15px);
/* fetch an image from the network to be used as a background image */
background-image: url('myimage.png');
```