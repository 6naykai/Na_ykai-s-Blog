---
title: HTML语言语法
date: 2023-04-17 16:56:13
updated: 2023-04-17 16:56:13
categories: HTML
---

## 1、设置字体加粗

```html
<b></b>中包含的字体就加粗了
<p><b>This text is bold</b>, but this text is not.</p>
```

## 2、设置代码块

```html
<code></code>中包含的内容就设置成代码了
<p><code>This text is bold</code>, but this text is not.</p>
```

## 3、插入图片

`<img src="" alt="">` 是HTML的插入图片语句，语法为：

```html
<img src="图片链接" alt="图片描述">
```

插入本地图片：在**项目根目录**下的 `source` 中新建一个 `img` 目录用于存放图片，将图片放在该目录下，使用 `../img/图片名` 引用

```html
<!-- md文件中能显示，但本地测试不可以展示 -->
<img src="../img/test.jpg" alt="text">
<!-- md文件中不能显示，但本地测试可以展示 -->
<img src="/img/test.jpg" alt="text">
```

插入网络图片：直接在“图片链接“中写入图片的网络链接就好

```html
<!-- 使用绝对路径插入网络图片（本地测试能展示出） -->
<img src="http://c.biancheng.net/cpp/templets/new/images/logo.jpg?v=3.994" alt="C语言中文网Logo"> <br>
<!-- 在当前 HTML 文档的上层目录中有一个 images 文件夹，该文件夹下有一张图片 html5.png -->
<img src="../images/html5.png" alt="HTML5 Logo">
```

对属性的说明：

- src 是必选属性，它是 source 的简称，用来指明图片的地址或者路径。src 支持多种图片格式，比如 jpg、png、gif 等。src 可以使用相对路径，也可以使用绝对路径。
- alt 是可选属性，用来定义图片的文字描述信息。当由于某些原因（例如图片路径错误、网络连接失败）导致图片无法加载时，就会显示 alt 属性中的信息。

