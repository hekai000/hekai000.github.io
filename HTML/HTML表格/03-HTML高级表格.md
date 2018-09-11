# HTML高级表格特性

## 使用caption为你的表格增加标题

```
<table>
  <caption>Dinosaurs in the Jurassic period</caption>

  ...
</table>
```
[HTMLcaption](../TEST_PROJ/HTML高级表格caption.html)

## 添加 \<thead\>, \<tfoot\>, 和 \<tbody\> 结构

由于你的表格在结构上有点复杂，如果把它们定义得更加结构化，那会帮助我们更能了解结构。
一个明确的方法是使用 \<thead\>, \<tfoot\>,和 \<tbody\>, 这些元素允许你把表格中的部分标记为表头、页脚、正文部分。

[HTMLthead](../TEST_PROJ/HTML高级表格thead.html)

## 嵌套表格

```
<table id="table1">
  <tr>
    <th>title1</th>
    <th>title2</th>
    <th>title3</th>
  </tr>
  <tr>
    <td id="nested">
      <table id="table2">
        <tr>
          <td>cell1</td>
          <td>cell2</td>
          <td>cell3</td>
        </tr>
      </table>
    </td>
    <td>cell2</td>
    <td>cell3</td>
  </tr>
  <tr>
    <td>cell4</td>
    <td>cell5</td>
    <td>cell6</td>
  </tr>
</table>
```

## 对于视力受损的用户的表格

### scope 属性

scope,可以添加在\<th\> 元素中，用来帮助屏幕阅读设备更好地理解那些标题单元格，这个标题单元格到底是列标题呢，还是行标题。
属性值有col/row/colgroup

```
 <thead>
  <tr>
    <th scope="col">Purchase</th>
    <th scope="col">Location</th>
    <th scope="col">Date</th>
    <th scope="col">Evaluation</th>
    <th scope="col">Cost (€)</th>
  </tr>
</thead>

<tr>
  <th scope="row">Haircut</th>
  <td>Hairdresser</td>
  <td>12/09</td>
  <td>Great idea</td>
  <td>30</td>
</tr>

```

### id和标题属性

如果要替代 scope 属性，可以使用 id 和 headers 属性来创造标题与单元格之间的联系。使用方法如下:

为每个\<th\> 元素添加一个 id (id 不能重复)。
为每个 \<td\> 元素添加一个 headers 属性。每个 headers 属性需要包含 th 元素的 id 。 
如果这个单元格是属于一个 th 元素下的，那么就需要包含 th 元素的 id 的值，如果属于多个 th 元素，那么可以用空格分隔这些 id。

```
<thead>
  <tr>
    <th id="purchase">Purchase</th>
    <th id="location">Location</th>
    <th id="date">Date</th>
    <th id="evaluation">Evaluation</th>
    <th id="cost">Cost (€)</th>
  </tr>
</thead>
<tbody>
<tr>
  <th id="haircut">Haircut</th>
  <td headers="location haircut">Hairdresser</td>
  <td headers="date haircut">12/09</td>
  <td headers="evaluation haircut">Great idea</td>
  <td headers="cost haircut">30</td>
</tr>

  ...

</tbody>
```