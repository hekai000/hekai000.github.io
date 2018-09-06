# HTML超链接

## 链接的解析

```
<a href="https://www.mozilla.org/en-US/"
   title="The best place to find more information about Mozilla's
          mission and how to contribute">the Mozilla homepage</a>.
```

## URL与PATH

- 统一资源定位器（英文：Uniform Resource Locator，简写：URL）是一个定义了在网络上的位置的一个文本字符串。

## 链接到文档片段

- 超链接可以链接到html文档的特定部分（被称为文档片段），而不仅仅是文件的顶部。要做到这一点你必须首先分配一个id属性的元素到链接。

```
链接到特定的id
<h2 id="Mailing_address">Mailing address</h2>
链接到另一个文件的特定的id
<p>Want to write us a letter? Use our <a href="contacts.html#Mailing_address">mailing address</a>.</p>
链接到同一份文件的另一部分
<p>The <a href="#Mailing_address">company mailing address</a> can be found at the bottom of this page.</p>
```

## 使用下载属性

当您链接到要下载的资源而不是在浏览器中打开时，您可以使用下载属性来提供一个默认的保存文件名
```
<a href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=en-US"
   download="firefox-latest-64bit-installer.exe">
  Download Latest Firefox for Windows (64-bit) (English, US)
</a>
```

## 电子邮件链接

```
<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
<a href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&amp;subject=The%20subject%20of%20the%20email &amp;body=The%20body%20of%20the%20email">
  Send mail with cc, bcc, subject and body
</a>
```