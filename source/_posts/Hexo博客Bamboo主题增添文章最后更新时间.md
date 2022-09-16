---
title: Hexo博客Bamboo主题增添文章最后更新时间
date: 2022-09-16 15:23:28
updated: 2022-09-16 15:23:28
categories: 前端
---

## 前言

<p style="text-indent:2em">建好了 Hexo 博客之后，发现一个问题：无法知道这篇文章最后更新于什么时候。可是搜索了谷歌、百度，发现修改方案基本上都是针对 Next 主题的，对我所用的 Bamboo 主题完全不适用，于是，搜索到了类似的 Hiker 主题的修改方式照着他的方式进行修改。下面讲述具体修改内容。</p>

## 调整 post 默认生成格式

<p style="text-indent:2em"> <code>post</code> 的生成模板在博客主目录下的 <code>scaffolds</code> 文件夹中，打开其中的 <code>post.md</code> 文件，修改成如下内容保存即可。</p>

```yaml
title: {{ title }}
date: {{ date }}
update: {{ date }}
```

<p style="text-indent:2em">这个时候可以生成一篇新的博客看看效果。然而你会发现虽然生成的新博客md文件中有 <code>update</code> 属性，但在网页上却看不到显示，这是因为 Bamboo 主题并没有配置 <code>update</code> 项。于是进行 Bamboo 主题的修改。</p>

## 修改Bamboo主题

### 修改相应的ejs文件

<p style="text-indent:2em">首先查看了 <code>/themes/hexo-theme-bamboo/layout</code> 文件夹下的 <code>post.ejs</code> 文件，发现7~9行显示如下代码信息：</p>

```ejs
<% if (page.imgTop !== false) { %>
  <%- partial('_partial/post/post-detail-header', { post: page }) %>
<% } %>
```

<p style="text-indent:2em">我们可以据此发现里面引入了 <code>_partial/post/post-detail-header</code> 的内容，于是在 <code>layout/_partial/post</code> 文件夹下找到 <code>post-detail-header.ejs</code> 文件，发现第39~43行显示如下代码：</p>

```ejs
	  <% if (post.date) { %>
        <span class="post-detail-header_date">
          <i class="fas fa-calendar"></i> <%= __('publishedIn') %>：<%- date(post.date, "YYYY-MM-DD") %> |
        </span>
      <% } %>
```

<p style="text-indent:2em">发现主题作者直接在这个ejs文件中引入了发布文件头部的时间，于是我们只需将 <code>update</code> 修改成上述代码类似模式添加在上述代码之下即可，修改后代码如下（注：下面展示结果包括了上述代码）</p>

```ejs
	  <% if (post.date) { %>
        <span class="post-detail-header_date">
          <i class="fas fa-calendar"></i> <%= __('publishedIn') %>：<%- date(post.date, "YYYY-MM-DD") %> |
        </span>
      <% } %>

      <!-- 增添update时间 -->
      <% if (post.update) { %>
        <span class="post-detail-header_update">
          <i class="fas fa-history"></i> <%= __('updated') %>：<%- date(post.update, "YYYY-MM-DD") %> |
        </span>
      <% } %>
```

<p style="text-indent:2em">如果你在此时重新使用“cgds大法”运行网站，会发现 <code>update</code> 属性已经可以显示出来了，但是它显示的是英文的 <code>updated</code> ，如果你想让它显示为你想让它显示为你想要的字，你有两种方式修改，一种是直接将上面代码中 <code>__('updated')</code> 单引号中的内容进行修改，但我更推荐第二种方式——增加字段。</p>

### 增加字段

<p style="text-indent:2em">由于你刚刚在 <code>post-detail-header.ejs</code> 文件中引入了 <code>updated</code> 字段，因此我们需要在语言文件中新增对应的字段，语言文件在 <code>hexo-theme-bamboo/languages</code> 中，修改你博客语言设置对应的yml文件，我的博客设置为中文，因此我以 <code>zh-CN.yml</code> 为例，打开该文件，找到第71行的 <code>publishedIn</code> 字段，在其下方新增 <code>updated</code> 字段，具体如下</p>

```yml
publishedIn: 发表于
updated: 更新于
```

<p style="text-indent:2em">字段后的文字可以自行修改，然后再次利用"cgds"大法运行网站，你就会发现已经成功添加了文章最后更新时间了！</p>
