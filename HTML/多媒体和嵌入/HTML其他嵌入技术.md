# 其他嵌入技术

 \<iframe\>, \<embed\> 和\<object\> 元素。
 \<iframe\>用于嵌入其他网页，另外两个元素则允许您嵌入PDF，SVG，甚至Flash — 一种正在被淘汰的技术，但您仍然会时不时的看到它。
 
 ## 嵌入类型的使用
 
 ```
 <iframe src="https://developer.mozilla.org/en-US/docs/Glossary"
        width="100%" height="500" frameborder="0"
        allowfullscreen sandbox>
  <p> <a href="https://developer.mozilla.org/en-US/docs/Glossary">
    Fallback link for browsers that don't support iframes
  </a> </p>
</iframe>
 ```
 在Firefox中，您会被告知：“X-Frame-Options拒绝加载https://developer.mozilla.org/en-US/docs/Glossary”。
 这是因为构建MDN的开发人员已经在网站页面的服务器上设置了一个不允许被嵌入到<iframe>的设置（请参阅配置CSP指令）这是有必要的 — 整个MDN页面被嵌入在其他页面中没有多大意义，除非您想要将其嵌入到您的网站上并将其声称为自己的内容，或尝试通过单击劫持来窃取数据，这都是非常糟糕的事情。此外，如果每个人都这样做，所有额外的带宽将花费Mozilla很多资金
 
 ## sandbox
 
 一个代码可以适当使用或用于测试的容器，但不能对其他代码库（意外或恶意）造成任何损害称为沙盒。
 
 未沙盒化(Unsandboxed)内容可以做得太多（执行JavaScript，提交表单，弹出窗口等）默认情况下，您应该使用没有参数的sandbox属性来强制执行所有可用的限制，如我们前面的示例所示。

如果绝对需要，您可以逐个添加权限（sandbox=""属性值内） - 请参阅sandbox所有可用选项的参考条目。其中重要的一点是，你永远不应该同时添加allow-scripts和allow-same-origin到你的sandbox属性中-在这种情况下，嵌入的内容可以绕过，从执行脚本停止网站同源安全策略，并使用JavaScript来关闭完全沙盒。

## CSP
配置CSP指令
CSP代表内容安全策略，它提供一组HTTP标头（由web服务器发送时与元数据一起发送的元数据），旨在提高HTML文档的安全性。在\<iframe\>安全性方面，您可以将服务器配置为发送适当的X-Frame-Options  标题。这样做可以防止其他网站在其网页中嵌入您的内容（这将导致点击和一系列其他攻击），正如我们之前看到的那样，MDN开发人员已经做了这些工作。
```
<meta http-equiv="Content-Security-Policy" content="default-src https:">
```

## \<embed\> 和 \<object\> 

\<embed\>和\<object\>元素的功能不同于\<iframe\>—— 这些元素是用来嵌入多种类型的外部内容的通用嵌入工具，其中包括像Java小程序和Flash，PDF（可在浏览器中显示为一个PDF插件）这样的插件技术，甚至像视频，SVG和图像的内容！

然而，您不太可能使用这些元素 - Applet几年来一直没有被使用；由于许多原因，Flash不再受欢迎（见下面的插件案例）；PDF更倾向于被链接而不是被嵌入；其他内容，如图像和视频都有更优秀、更容易元素来处理。插件和这些嵌入方法真的是一种传统技术，我们提及它们主要是为了以防您在某些情况下遇到问题，比如内部网或企业项目等。


|说明|\<embed\>	|\<object\>|
|:---:|:---:|:---:|
|嵌入内容的网址	|src	|data|
|嵌入内容的准确媒体类型	|type	|type|
|由插件控制的框的高度和宽度（以CSS像素为单位）|	height width|	height width|
|名称和值，将插件作为参数提供|	具有这些名称和值的ad hoc属性|	单标签\<param\>元素，包含在内\<object\>|
|独立的HTML内容作为不可用资源的回退|	不支持（\<noembed\>已过时）|	包含在元素\<object\>之后\<param\>|

\<object\>需要data属性，type属性或两者。
如果您同时使用这两个，您也可以使用该typemustmatch属性（仅在Firefox中实现，在本文中）。
typemustmatch保持嵌入文件不运行，除非type属性提供正确的媒体类型。
因此，当您嵌入来自不同来源的内容（可以防止攻击者通过插件运行任意脚本）时，可以赋予重要的安全优势。
```
<embed src="whoosh.swf" quality="medium"
       bgcolor="#ffffff" width="550" height="400"
       name="whoosh" align="middle" allowScriptAccess="sameDomain"
       allowFullScreen="false" type="application/x-shockwave-flash"
       pluginspage="http://www.macromedia.com/go/getflashplayer">
```

```
<object data="mypdf.pdf" type="application/pdf"
        width="800" height="1200" typemustmatch>
  <p>You don't have a PDF plugin, but you can <a href="myfile.pdf">download the PDF file.</a></p>
</object>
```

插件是一种对浏览器原生无法读取的内容提供访问权限的软件