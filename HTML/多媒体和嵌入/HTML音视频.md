# 音视频

## video标签

```
<video src="rabbit320.webm" controls>
  <p>Your browser doesn't support HTML5 video. Here is a <a href="rabbit320.webm">link to the video</a> instead.</p> 
</video>
```

- src
同 \<img\> 标签使用方式相同，src 属性指向你想要嵌入网页当中的视频资源，他们的使用方式完全相同。

- controls
用户必须能够控制视频和音频的回放功能。你可以使用浏览器提供的控制接口，同时你也可以在 JavaScript （JavaScript API）当中使用这些控制接口。至少，这些媒体应该包括开始和停止，以及调整音量的功能。

- \<video\> 标签内的段落
这个叫做后备内容 — 当浏览器不支持 \<video\> 标签的时候，它将会显示出来，它使我们能够对旧的浏览器做一些兼容处理。你可以添加任何后备内容，在这个例子中我们提供了一个指向这个视频文件的链接，从而使用户可以至少访问到这个文件，而不会局限于浏览器的支持。

## 多格式支持

像 MP3、MP4、WebM这些术语叫做容器格式。他们是用不同的方式来播放音频或者视频的 — 也就是说这些容器是用不同的音频轨道、视频轨道、元数据来呈现媒体文件的。
- WebM 容器通常包括了 Ogg Vorbis 音频和 VP8/VP9 视频。主要在 FireFox 和 Chrome 当中支持。
- MP4 容器通常包括 AAC 以及 MP3 音频和 H.264 视频。主要在 Internet Explorer 和 Safari 当中支持。
- 老式的 Ogg 容器往往支持 Ogg Vorbis  音频和 Ogg Theora 视频。主要在 Firefox 和 Chrome 当中支持，不过这个容器已经被更强大的 WebM 容器所取代。

```
<video controls>
  <source src="rabbit320.mp4" type="video/mp4">
  <source src="rabbit320.webm" type="video/webm">
  <p>Your browser doesn't support HTML5 video. Here is a <a href="rabbit320.mp4">link to the video</a> instead.</p>
</video>
```

现在我们将 src 属性从 \<video\> 标签中移除，转而将它放在几个单独的标签 \<source\> 当中。在这个例子当中，浏览器将会检查 \<source\> 标签，并且播放第一个与其自身 codec 相匹配的媒体。你的视频应当包括 WebM 和 MP4 两种格式，这两种在目前已经足够支持大多数平台和浏览器。

每个 \<source\> 标签页含有一个 type 属性，这个属性是可选的，但是建议你添加上这个属性 — 它包含了视频文件的 MIME types ，同时浏览器也会通过检查这个属性来迅速的跳过那些不支持的格式。如果你没有添加 type 属性，浏览器会尝试加载每一个文件，直到找到一个能正确播放的格式，这样会消耗掉大量的时间和资源。

```
<video controls width="400" height="400"
       autoplay loop muted
       poster="poster.png">
  <source src="rabbit320.mp4" type="video/mp4">
  <source src="rabbit320.webm" type="video/webm">
  <p>Your browser doesn't support HTML5 video. Here is a <a href="rabbit320.mp4">link to the video</a> instead.</p>
</video>
```

新的特性：

- width 和 height
你可以用属性控制视频的尺寸，也可以用 CSS 来控制视频尺寸。 无论使用哪种方式，视频都会保持它原始的长宽比 — 也叫做纵横比。如果你设置的尺寸没有保持视频原始长宽比，那么视频边框将会拉伸，而未被视频内容填充的部分，将会显示默认的背景颜色。

- autoplay
这个属性会使音频和视频内容立即播放，即使页面的其他部分还没有加载完全。建议不要应用这个属性在你的网站上，因为用户们会比较反感自动播放的媒体文件。

- loop
这个属性可以让音频或者视频文件循环播放。同样不建议使用，除非有必要。

- muted
这个属性会导致媒体播放时，默认关闭声音。

- poster
这个属性指向了一个图像的URL，这个图像会在视频播放前显示。通常用于粗略的预览或者广告。

- preload
这个属性被用来缓冲较大的文件，有3个值可选：

1. "none" ：不缓冲
2. "auto" ：页面加载后缓存媒体文件
3. "metadata" ：仅缓冲文件的元数据

## audio标签

与 HTML5 \<video\> 的差异如下：

\<audio\> 标签不支持 width/height 属性 — 由于其并没有视觉部件，也就没有可以设置 width/height 的内容。
同时也不支持 poster 属性 — 同样，没有视觉部件。
除此之外，\<audio\> 标签支持所有 \<video\> 标签拥有的特性

## 显示音轨文本

HTML5 <video> 使之成为可能，有了 WebVTT 格式，你可以使用 <track> 标签。

WebVTT 是一个格式，用来编写文本文件，这个文本文件包含了众多的字符串，这些字符串会带有一些元数据，它们可以用来描述这个字符串将会在视频中显示的时间，甚至可以用来描述这些字符串的样式以及定位信息。这些字符串叫做 cues ，你可以根据不同的需求来显示不同的样式，最常见的如下：

- subtitle
通过添加翻译字幕，来帮助那些听不懂外国语言的人们理解音频当中的内容。

- captions
同步翻译对白，或是描述一些有重要信息的声音，来帮助那些不能听音频的人们理解音频中的内容。

- timed descriptions
将文字转换为音频，用于服务那些有视觉障碍的人。

```
WEBVTT

1
00:00:22.230 --> 00:00:24.606
This is the first subtitle.

2
00:00:30.739 --> 00:00:34.074
This is the second.

  ...
```

让其与 HTML 媒体一起显示，你需要做如下工作：

以 .vtt 后缀名保存文件。
用 <track> 标签链接 .vtt 文件， <track> 标签需放在 <audio> 或 <video> 标签当中，同时需要放在所有 <source> 标签之后。使用 kind 属性来指明是哪一种类型，如 subtitles 、 captions 、 descriptions。然后，使用 srclang 来告诉浏览器你是用什么语言来编写的 subtitles。

```
<video controls>
    <source src="example.mp4" type="video/mp4">
    <source src="example.webm" type="video/webm">
    <track kind="subtitles" src="subtitles_en.vtt" srclang="en">
</video>
```

标注为default的<track>表示默认使用的字幕。如果默认不使用任何字幕，则都不设置default