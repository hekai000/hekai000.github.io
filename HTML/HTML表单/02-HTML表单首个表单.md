# 首个表单

##　HTML表单

HTML表单是用户和web站点或应用程序之间交互的主要内容之一。它们允许用户将数据发送到web站点。

##　主动学习

### 相关元素

```
<form>
<label>
<input>
<textarea>
<button>
```

### form元素

\<form\>元素

这个元素正式定义了一个表单。
就像\<div\>元素或\<p\>元素，它是一个容器元素，但它也支持一些特定的属性来配置表单的行为方式。
它的所有属性都是可选的，但至少要设置action属性和method属性，这被认为是最佳实践。

- action 属性定义了在提交表单时所收集的数据的位置(URL)。.
- method 属性定义了发送数据的HTTP方法(它可以是“get”或“post”).

### button
您将看到\<button\>元素也接受一个 type属性，它接受三个值中的一个:submit, reset或者 button。

- 单击 submit 按钮 发送表单的数据到\<form\>元素的action 属性所定义的网页。
- 单击 reset 按钮 将所有表单小部件重新设置为它们的默认值。从用户体验的角度来看，这被认为是一种糟糕的做法。
- 单击button 按钮……不会发生任何事！这听起来很傻，但是用JavaScript构建定制按钮非常有用。 


### div/input/textarea

- \<div\> 元素可以方便地构造我们的代码，使样式更简单。

- 注意在所有\<label\>元素上使用for属性；它是将标签链接到表单小部件的一种正式方式。这个属性引用相应的小部件的id。这样做有一些好处。最明显的一个好处是允许用户单击标签以激活相应的小部件

- 在 \<input\>元素中，最重要的属性是type 属性。这个属性非常重要，因为它定义了\<input\>属性的行为方式。它可以从根本上改变元素。

    text 作为第一个输入——这个属性的默认值。它表示一个基本的单行文本字段，接受任何类型的文本输入。
    对于第二个输入，我们使用值email，它定义了一个只接受格式良好的电子邮件地址的单行文本字段。
    最后一个值将一个基本的文本字段转换为一种“智能”字段，该字段将对用户输入的数据进行一些检查。
- \<input\> 标签是一个空元素，这意味着它不需要关闭标签。相反， \<textarea\>不是一个空元素，因此必须使用适当的结束标记来关闭它。
这对HTML表单的特定特性有影响:定义默认值的方式。要定义\<input\>的默认值，你必须使用value 属性.

### 向web服务器发送表单数据

要将数据命名为表单，您需要在每个表单小部件上使用 name 属性来收集特定的数据块。让我们再来看看我们的表单代码:

```
<form action="/my-handling-form-page" method="post"> 
  <div>
    <label for="name">Name:</label>
    <input type="text" id="name" name="user_name" />
  </div>
  <div>
    <label for="mail">E-mail:</label>
    <input type="email" id="mail" name="user_email" />
  </div>
  <div>
    <label for="msg">Message:</label>
    <textarea id="msg" name="user_message"></textarea>
  </div>

```

每当您有一组单选按钮时，您应该将它们嵌套在\<fieldset\>元素中。
还有其他用例，一般来说，\<fieldset\>元素也可以用来对表单进行分段。
理想情况下，长表单应该在多个页面之间进行拆分，但是如果表单很长，但必须在单个页面上，那么在不同的fieldsets中放置不同的相关部分可以提高可用性。

### label

```
<form>
  <p>
    <label for="taste_1">I like cherry</label>
    <input type="checkbox" id="taste_1" name="taste_cherry" value="1">
  </p>
  <p>
    <label for="taste_2">I like banana</label>
    <input type="checkbox" id="taste_2" name="taste_banana" value="2">
  </p>
</form>
```

label的for标签与input的id相关联




