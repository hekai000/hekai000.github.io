# HTML高级文字格式

## 描述列表

描述列表使用与其他列表类型不同的闭合标签— <dl>; 
此外，每一项都用  <dt> (description term)  元素闭合。
每个描述都用 <dd> (description description) 元素闭合。
一个术语<dt>可以同时有多个描述<dd>
```
<dl>
<dt></dt>
<dd></dd>
</dl>
```

## 引用

### 块引用

如果一个块级内容（一个段落、多个段落、一个列表等）从其他地方被引用，你应该把它用<blockquote>元素包裹起来表示，
并且在cite属性里用URL来指向引用的资源。

```
<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
  <p>The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block
  Quotation Element</em>) indicates that the enclosed text is an extended quotation.</p>
</blockquote>
```

### 行内引用

行内元素用同样的方式工作，除了使用<q>元素。

```
<p>The quote element — <code>&lt;q&gt;</code> — is <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">intended
for short quotations that don't require paragraph breaks.</q></p>
```

### 引文

cite属性的内容听起来很有用，但不幸的是，浏览器、屏幕阅读器等等不会真的关心它，如果不使用JavaScript或CSS，浏览器不会显示cite的内容。如果你想要确保引用的资源在页面上是可用的，
更好的方法是把<cite>元素放到引用元素旁边，比如
```
<a><cite>xxx<cite><a>
```
这就意味着包含引用资源的名称——即引用的书的名字，或人的名字——但并不表示你不可以用同样的方式把要链接的文本放到<cite>元素中
引文默认的字体样式为斜体

### 缩略语

\<abbr\>——它常被用来包裹一个缩略语或缩写，并且提供缩写的解释（包含在title属性中）
```
<p>We use <abbr title="Hypertext Markup Language">HTML</abbr> to structure our web documents.</p>
```

### 标记联系方式

HTML有个用于标记联系方式的元素——<address>。它仅仅包含你的联系方式
<address>元素是为了标记编写HTML文档的人的联系方式，而不是任何其他的内容。

### 上标和下标

```
<sup>上标
<sub>下标
```

### 展示计算机代码

\<code\>: 用于标记计算机通用代码。
\<pre\>: 对保留的空格（通常是代码块）——如果您在文本中使用缩进或多余的空白，浏览器将忽略它，您将不会在呈现的页面上看到它。但是，如果您将文本包含在<pre></pre>标签中，那么空白将会以与你在文本编辑器中看到的相同的方式渲染出来。
\<var\>: 用于标记具体变量名。
\<kbd\>: 用于标记输入电脑的键盘（或其他类型）输入。
\<samp\>: 用于标记计算机程序的输出。

```
<pre><code>var para = document.querySelector('p');

para.onclick = function() {
  alert('Owww, stop poking me!');
}</code></pre>

<p>You shouldn't use presentational elements like <code>&lt;font&gt;</code> and <code>&lt;center&gt;</code>.</p>

<p>In the above JavaScript example, <var>para</var> represents a paragraph element.</p>


<p>Select all the text with <kbd>Ctrl</kbd>/<kbd>Cmd</kbd> + <kbd>A</kbd>.</p>

<pre>$ <kbd>ping mozilla.org</kbd>
<samp>PING mozilla.org (63.245.215.20): 56 data bytes
64 bytes from 63.245.215.20: icmp_seq=0 ttl=40 time=158.233 ms</samp></pre>
```

### 标记日期和时间

HTML 还支持将时间和日期标记为可供机器识别的格式的 <time> 元素
```
<time datetime="2016-01-20">20 January 2016</time>
```