# 框模型

## 框属性

width 和 height
width 和 height 设置内容框（content box）的宽度和高度。内容框是框内容显示的区域——包括框内的文本内容，以及表示嵌套子元素的其它框。

注意: 还有其他属性可以更巧妙地处理内容的大小——设置大小约束而不是绝对的大小。这些属性包括min-width、max-width、min-height 和 max-height。

padding
padding 表示一个 CSS 框的内边距 ——这一层位于内容框的外边缘与边界的内边缘之间。该层的大小可以通过简写属性padding 一次设置所有四个边，或用 padding-top、padding-right、padding-bottom 和 padding-left 属性一次设置一个边。
border
CSS 框的边界（border）是一个分隔层，位于内边距的外边缘以及外边距的内边缘之间。边界的默认大小为0——从而让它不可见——不过我们可以设置边界的厚度、风格和颜色让它出现。 border 简写属性可以让我们一次设置所有四个边，例如  border: 1px solid black; 但这个简写可以被各种普通书写的更详细的属性所覆盖：
border-top, border-right, border-bottom, border-left: 分别设置某一边的边界厚度／风格／颜色。
border-width, border-style, border-color: 分别仅设置边界的厚度／风格／颜色，并应用到全部四边边界。
你也可以单独设置某一个边的三个不同属性，如 border-top-width, border-top-style, border-top-color，等。 
margin
外边距（margin）代表 CSS 框周围的外部区域，称为外边距，它在布局中推开其它 CSS 框。其表现与 padding 很相似；简写属性为 margin，单个属性分别为 margin-top、margin-right、margin-bottom 和 margin-left。

注意: 外边距有一个特别的行为被称作外边距塌陷（margin collapsing）：当两个框彼此接触时，它们的间距将取两个相邻外边界的最大值，而非两者的总和。

框的高度不遵守百分比的长度；框的高度总是采用框内容的高度，除非指定一个绝对的高度（如：px 或者em），它会比在页面上默认是100%高度更实用。
border也忽略百分比宽度设置。
你应该注意的是框的总宽度是width, padding-right, padding-left, border-right, 以及 border-left 属性之和。在一些情况下比较恼人（例如，假使你想要一个框占窗口宽度的50%，但边界和内边距是用像素来表示时该怎么办？），为了避免这种问题，有可能使用属性box-sizing来调整框模型。使用值border-box，它将框模型更改成这个新的模型：


## 高级的框操作

### 溢流

当你使用绝对的值设置了一个框的大小（如，固定像素的宽/高），允许的大小可能不适合放置内容，这种情况下内容会从盒子溢流。
我们使用overflow属性来控制这种情况的发生。它有一些可能的值，但是最常用的是：

auto: 当内容过多，溢流的内容被隐藏，然后出现滚动条来让我们滚动查看所有的内容。
hidden: 当内容过多，溢流的内容被隐藏。
visible: 当内容过多，溢流的内容被显示在盒子的外边（这个是默认的行为）

### 背景裁剪（Background clip）

```
.default     { background-clip: border-box;  }
.padding-box { background-clip: padding-box; }
.content-box { background-clip: content-box; }
```

### 轮廓(Outline)

一个框的 outline 是一个看起来像是边界但又不属于框模型的东西。它的行为和边界差不多，但是并不改变框的尺寸

## CSS 框类型

- 块框（ block box）是定义为堆放在其他框上的框（例如：其内容会独占一行），而且可以设置它的宽高，之前所有对于框模型的应用适用于块框 （ block box）
- 行内框（ inline box）与块框是相反的，它随着文档的文字（例如：它将会和周围的文字和其他行内元素出现在同一行，而且它的内容会像一段中的文字一样随着文字部分的流动而打乱），对行内盒设置宽高无效，设置padding, margin 和 border都会更新周围文字的位置，但是对于周围的的块框（ block box）不会有影响。
- 行内块状框（inline-block box） 像是上述两种的集合：它不会重新另起一行但会像行内框（ inline box）一样随着周围文字而流动，而且他能够设置宽高，并且像块框一样保持了其块特性的完整性，它不会在段落行中断开。
