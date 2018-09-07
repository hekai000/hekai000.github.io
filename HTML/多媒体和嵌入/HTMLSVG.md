# SVG

## 概念

- 位图使用像素网格来定义 — 
一个位图文件精确得包含了每个像素的位置和它的色彩信息。
流行的位图格式包括 Bitmap (.bmp), PNG (.png), JPEG (.jpg), and GIF (.gif.)

- 矢量图使用算法来定义 — 
一个矢量图文件包含了图形和路径的定义，电脑可以根据这些定义计算出当它们在屏幕上渲染时应该呈现的样子。 
SVG 格式可以让我们创造用于 Web 的精彩的矢量图形。

## 使用方式

1. 快捷方式：\<img\>

```
<img 
    src="equilateral.svg" 
    alt="triangle with all three sides equal"
    height="87px"
    width="100px" />
    

```

- 优点
快速，熟悉的图像语法与alt属性中提供的内置文本等效。
可以通过在\<a\>元素嵌套\<img\>，使图像轻松地成为超链接。
- 缺点
无法使用JavaScript操作图像。
如果要使用CSS控制SVG内容，则必须在SVG代码中包含内联CSS样式。 （从SVG文件调用的外部样式表不起作用）
不能用CSS伪类来重设图像样式（如:focus）。

对于不支持SVG（IE 8及更低版本，Android 2.3及更低版本）的浏览器，您可以从src属性引用PNG或JPG，并使用srcset属性 只有最近的浏览器才能识别）来引用SVG。
 在这种情况下，仅支持浏览器将加载SVG - 较旧的浏览器将加载PNG：
```
 <img src="equilateral.png" alt="triangle with equal sides" srcset="equilateral.svg">
```

您还可以使用SVG作为CSS背景图像，如下所示。 在下面的代码中，旧版浏览器会坚持他们理解的PNG，而较新的浏览器将加载SVG：
```
background: url("fallback.png") no-repeat center;
background-image: url("image.svg");
background-size: contain;
```

2. 内联SVG
你还可以在文本编辑器中打开SVG文件，复制SVG代码，并将其粘贴到HTML文档中 - 这有时称为将SVG内联或内联SVG。
确保您的SVG代码在\<svg\>\</svg\>标签中（不要在外面添加任何内容）。这是一个非常简单的示例，您可以粘贴到文档中：
```
<svg width="300" height="200">
    <rect width="100%" height="100%" fill="green" />
</svg>
```

- 优点
将 SVG 内联减少 HTTP 请求，可以减少加载时间。
您可以为 SVG 元素分配class和id，并使用 CSS 修改样式，无论是在SVG中，还是 HTML 文档中的 CSS 样式规则。 实际上，您可以使用任何 SVG外观属性 作为CSS属性。
内联SVG是唯一可以让您在SVG图像上使用CSS交互（如:focus）和CSS动画的方法（即使在常规样式表中）。
您可以通过将 SVG 标记包在\<a\>元素中，使其成为超链接。

- 缺点
这种方法只适用于在一个地方使用的SVG。多次使用会导致资源密集型维护（resource-intensive maintenance）。
额外的 SVG 代码会增加HTML文件的大小。
浏览器不能像缓存普通图片一样缓存内联SVG。
您可能会在\<foreignObject\> 元素中包含回退，但支持 SVG 的浏览器仍然会下载任何后备图像。你需要考虑仅仅为支持过时的浏览器，而增加额外开销是否真的值得。

3. iframe中嵌入SVG

您可以在浏览器中打开 SVG 图像，就像网页一样。 因此，使用<iframe>嵌入 SVG 文档就像我们在 从对象到iframe - 其他嵌入技术 中进行研究一样。

```
<iframe src="triangle.svg" width="500" height="500" sandbox>
    <img src="triangle.png" alt="Triangle with three unequal sides" />
</iframe>
```

- 缺点
如你所知， iframe有一个回退机制，如果浏览器不支持iframe，则只会显示回退。
此外，除非 SVG 和您当前的网页具有相同的 origin，否则你不能在主页面上使用 JavaScript 来操纵 SVG。