# HTML的图片

## img

### src

### alt替换文本

### width和height

如果你需要改变图片的尺寸，你应该使用CSS而不是HTML。

### title

可以给图片增加title属性来提供需要更进一步的支持信息

## figure

图片搭配文字说明，使用 HTML5 的 <figure> 和 <figcaption> 元素，它正是为此而被创造出来的：为图片提供一个语义容器，在标题和图片之间建立清晰的关联。
```
<figure>
  <img src="images/dinosaur.jpg"
       alt="The head and torso of a dinosaur skeleton;
            it has a large head with long sharp teeth"
       width="400"
       height="341">

  <figcaption>A T-Rex on display in the Manchester University Museum.</figcaption>
</figure>
```

注意 \<figure\> 里不一定要是一张图片，只要是一个这样的独立内容单元：

- 用紧凑、易于掌握的方式表达你的意图。
- 可以放在页面线性流的中几个地方（Could go in several places in the page's linear flow）
为主要内容提供重要的补充说明。
- \<figure\> 可以是几张图片、一段代码、音视频、方程、表格或别的。

## CSS背景图片

```
p {
  background-image: url("images/dinosaur.jpg");
}
```
总而言之，如果图像对您的内容里有意义，则应使用HTML图像。 如果图像纯粹是装饰，则应使用CSS背景图片。