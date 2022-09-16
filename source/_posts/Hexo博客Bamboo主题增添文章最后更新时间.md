---
title: Hexo博客Bamboo主题增添文章最后更新时间
date: 2022-09-16 15:23:28
update: 2022-09-16 15:23:28
categories: 前端
---

## 前言

​        建好了 Hexo 博客之后，发现一个问题：无法知道这篇文章最后更新于什么时候。可是搜索了谷歌、百度，发现修改方案基本上都是针对 Next 主题的，对我所用的Bamboo主题完全不适用，于是，搜索到了类似的Hiker 主题的修改方式照着他的方式进行修改。下面讲述具体修改内容。

## 调整post默认生成格式

​		post的生成模板在博客主目录下的scaffolds文件夹中，打开其中的post.md文件，修改成如下内容保存即可。

```yaml
title: {{ title }}
date: {{ date }}
update: {{ date }}
```

​		这个时候可以生成一篇新的博客看看效果。然而你会发现虽然生成的新博客md文件中有update属性，但在网页上却看不到显示，这是因为Bamboo主题并没有配置update项。于是进行Bamboo主题的修改。

## 修改Bamboo主题

### 修改相应的ejs文件

​		首先查看了/themes/hexo-theme-bamboo/layout文件夹下的post.ejs文件，发现7~9行显示如下代码信息：

```ejs
<% if (page.imgTop !== false) { %>
  <%- partial('_partial/post/post-detail-header', { post: page }) %>
<% } %>
```

​		我们可以据此发现里面引入了 _partial/post/post-detail-header的内容，于是在layout/ _partial/post文件夹下找到post-detail-header.ejs文件，发现第39~43行显示如下代码：

```ejs
	  <% if (post.date) { %>
        <span class="post-detail-header_date">
          <i class="fas fa-calendar"></i> <%= __('publishedIn') %>：<%- date(post.date, "YYYY-MM-DD") %> |
        </span>
      <% } %>
```

​		发现主题作者直接在这个ejs文件中引入了发布文件头部的时间，于是我们只需将update修改成上述代码类似模式添加在上述代码之下即可，修改后代码如下（注：下面展示结果包括了上述代码）

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

​		如果你在此时重新使用“cgds大法”运行网站，会发现update属性已经可以显示出来了，但是它显示的是英文的updated，如果你想让它显示为你想让它显示为你想要的字，你有两种方式修改，一种是直接将上面代码中 __('updated')单引号中的内容进行修改，但我更推荐第二种方式——增加字段。

### 增加字段

​		由于你刚刚在post-detail-header.ejs文件中引入了updated字段，因此我们需要在语言文件中新增对应的字段，语言文件在hexo-theme-bamboo/languages中，修改你博客语言设置对应的yml文件，我的博客设置为中文，因此我以zh-CN.yml为例，打开该文件，找到第71行的publishedIn字段，在其下方新增updated字段，具体如下

```yml
publishedIn: 发表于
updated: 更新于
```

​		字段后的文字可以自行修改，然后再次利用"cgds"大法运行网站，你就会发现已经成功添加了文章最后更新时间了！
