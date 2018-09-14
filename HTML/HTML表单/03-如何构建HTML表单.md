# 如何构建HTML表单

## form元素

1.  \<form\> 元素按照一定的格式定义了表单和确定表单行为的属性。当您想要创建一个HTML表单时，都必须从这个元素开始，然后把所有内容都放在里面

2. 严格禁止在一个表单内嵌套另一个表单。嵌套会使表单的行为不可预知，而取决于正在使用的浏览器。

## filedset 和 legend元素

\<fieldset\>元素是一种方便的用于创建具有相同目的的小部件组的方式，出于样式和语义目的。 
你可以在\<fieldset\>开口标签后加上一个 \<legend\>元素来给\<fieldset\> 标上标签。 
\<legend\>的文本内容正式地描述\<fieldset\>的用途。它是包含在\<fieldset\>里的。

```
<form>
  <fieldset>
    <legend>Fruit juice size</legend>
    <p>
      <input type="radio" name="size" id="size_1" value="small">
      <label for="size_1">Small</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_2" value="medium">
      <label for="size_2">Medium</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_3" value="large">
      <label for="size_3">Large</label>
    </p>
  </fieldset>
</form>

```