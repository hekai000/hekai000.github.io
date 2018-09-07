# HTML自适应图片

## 自适应图片解决的两大问题

1. 艺术方向问题   不同的设备显示不同的图片
2. 分辨率切换问题 根据设备的大小，提供不同尺寸的图片或者不同分辨率的图片

## 怎样创建自适应图片

### 分辨率切换，不同的尺寸
```
<img srcset="elva-fairy-320w.jpg 320w,
             elva-fairy-480w.jpg 480w,
             elva-fairy-800w.jpg 800w"
     sizes="(max-width: 320px) 280px,
            (max-width: 480px) 440px,
            800px"
     src="elva-fairy-800w.jpg" alt="Elva dressed as a fairy">
```
srcset定义了我们允许浏览器选择的图像集，以及每个图像的大小。在每个逗号之前，我们写：

- 一个文件名 (elva-fairy-480w.jpg.)
- 一个空格
- 图像的固有宽度（以像素为单位）（480w）——注意到这里使用w单位，而不是你预计的px。这是图像的真实大小，可以通过检查你电脑上的图片文件找到

sizes定义了一组媒体条件（例如屏幕宽度）并且指明当某些媒体条件为真时，什么样的图片尺寸是最佳选择—我们在之前已经讨论了一些提示。在这种情况下，在每个逗号之前，我们写：

- 一个媒体条件（(max-width:480px)）——你会在 CSS topic中学到更多的。但是现在我们仅仅讨论的是媒体条件描述了屏幕可能处于的状态。在这里，我们说“当视窗的宽度是480像素或更少”。
- 一个空格
- 当媒体条件为真时，图像将填充的槽的宽度（440px）

- 查看设备宽度
- 检查sizes列表中哪个媒体条件是第一个为真
- 查看给予该媒体查询的槽大小
- 加载srcset列表中引用的最接近所选的槽大小的图像

Chrome 不支持
Firefox 支持

### 分辨率切换，相同的尺寸

如果你支持多种分辨率显示，但希望每个人在屏幕上看到的图片的实际尺寸是相同的，你可以让浏览器通过srcset和x语法结合——一种更简单的语法——而不用sizes，来选择适当分辨率的图片。
```
<img srcset="elva-fairy-320w.jpg,
             elva-fairy-480w.jpg 1.5x,
             elva-fairy-640w.jpg 2x"
     src="elva-fairy-640w.jpg" alt="Elva dressed as a fairy">
```


### 艺术方向问题

艺术方向是指使用 picture 元素，根据设备特性选择特定图像。
picture 元素支持声明式方式定义，根据设备大小、设备分辨率、屏幕方向等不同特性来提供一个图片的多尺寸版本：

\<picture\>元素

```
<picture>
  <source media="(max-width: 799px)" srcset="elva-480w-close-portrait.jpg">
  <source media="(min-width: 800px)" srcset="elva-800w.jpg">
  <img src="elva-800w.jpg" alt="Chris standing up holding his daughter Elva">
</picture>
```

- \<source\>元素包含一个media属性，这一属性包含一个媒体条件——就像第一个srcset例子，这些条件来决定哪张图片会显示——第一个条件返回真，那么就会显示这张图片。在这种情况下，如果视窗的宽度为799px或更少，第一个\<source\>元素的图片就会显示。如果视窗的宽度是800px或更大，就显示第二张图片。

- srcset属性包含要显示图片的路径。请注意，正如我们在\<img\>上面看到的那样，\<source\>可以使用引用多个图像的srcset属性，还有sizes属性。所以你可以通过一个 \<picture\>元素提供多个图片，不过也可以给每个图片提供多分辨率的图片。实际上，你可能不想经常做这样的事情。

- 在任何情况下，你都必须在 \</picture\>之前正确提供一个\<img\>元素以及它的src和alt属性，否则不会有图片显示。当媒体条件都不返回真的时候（你可以在这个例子中删除第二个\<source\> 元素），它会提供图片；如果浏览器不支持 \<picture\>元素时，它可以作为后备方案。

### 为什么不能使用CSS或JS来自适应图片

当浏览器开始加载一个页面, 它会先下载 (预加载) 任意的图片，这是发生在主解析器开始加载和解析页面的 CSS 和 JavaScript 之前的。
这是一个非常有用的技巧，平均来说，页面加载的时间少了 20%。
但是, 这对响应式图片一点帮助都没有, 所以需要实现类似 srcset的方法。
因为你不能先加载好 \<img\> 元素后, 再用 JavaScript 检测视图的宽度，如果觉得大小不合适，就动态地加载小的图片替换已经加载好的图片，
这样的话, 原始的图像已经被加载了, 然后你也加载了小的图像, 这样的做法对于响应式图像的理念来说，是很糟糕的。

### 使用现代图像格式

```
<picture>
  <source type="image/svg+xml" srcset="pyramid.svg">
  <source type="image/webp" srcset="pyramid.webp"> 
  <img src="pyramid.png" alt="regular pyramid built from four equilateral triangles">
</picture>
```

- 不要使用media属性，除非你也需要艺术方向。
- 在\<source\> 元素中，你只可以引用在type中声明的文件类型。
- 像之前一样，如果必要，你可以在srcset和sizes中使用逗号分割的列表。

## 总结

- 艺术方向：当你想为不同布局提供不同剪裁的图片——比如在桌面布局上显示完整的、横向图片，而在手机布局上显示一张剪裁过的、突出重点的纵向图片，
可以用 \<picture\> 元素来实现。

- 分辨率切换：当你想要为窄屏提供更小的图片时，因为小屏幕不需要像桌面端显示那么大的图片；
以及你想为高/低分辨率屏幕提供不同分辨率的图片时，都可以通过 vector graphics (SVG images)、 srcset 以及 sizes 属性来实现。