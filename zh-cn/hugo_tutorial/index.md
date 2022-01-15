# Hugo网站搭建经验帖


<!--more-->
<!-- ![](/images/Hugo-Logo.png "A blog that shares some of my own experiences with building Hugo website.") -->

## 1. 前提

1. 安装 [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. 安装 [hugo](https://gohugo.io/getting-started/quick-start/)

## 2. 开始

我建议查看官方文档，了解基本的安装和配置。如果到那时你还不能解决问题，那就看看那些可能会有帮助的博客文章。

### 官方文档

* https://hugoloveit.com/（网站小样）
* https://gohugo.io/getting-started/quick-start/
* https://hugoloveit.com/（这是 Hugo 中的 loveit 主题，但是格式和debug应该能应用到其他模板）
* [YouTube 一步一步的教程](https://www.youtube.com/watch?v=5GnFZ8XpMak)

### 博客

* [有没有地方我们可以在 blogdown 中放置非博客文件（pdf 文件）？](https://community.rstudio.com/t/is-there-a-place-we-can-put-non-blog-files-pdf-files-in-blogdown/10138/3)
* [如何用Hugo一起创建多语言网站](https://yonkov.github.io/post/how-to-make-a-mulilingual-website-with-hugo/)

### 杂项

* [font_awesome。Docset（图标）](https://kapeli.com/cheat_sheets/Font_Awesome.docset/Contents/Resources/Documents/index)

{{< admonition note "Common Issues" >}}
* 如果你的页面在开发模式下崩溃，请耐心等待，也许可以用 ```Ctrl-C``` 和 ```hugo server -D``` 在终端中重新加载服务器。
* 要注意语法、格式，特别是在使用多语言设置时。
* 如果你不确定组织结构，请在复制每个 Hugo Repo 文件夹后，始终首先引用 themes/xxx/examplesite 文件夹。
* 当你想要在主页中为内容预览添加图像时，请执行以下操作:
  ``` Markdown
  resources:
  - name: "featured-image"
    src: "featured-image.png" 
  ```
  并将你的 MD 文件命名为 ```index.md```。如果你想告诉 Hugo 在预览中只在分隔符之前总结内容，请不要忘记添加 ```<!--more-->``` 分隔符。{{< /admonition >}}

## 3. 发布你的网站

出版这一页对我来说有点麻烦。在这次体验之后，我真诚的建议是找一个教程，并严格按照步骤进行。即使你不喜欢这个主题或教程风格，但首先建立你的理解并在此基础上进行升级/优化总是比较容易的。

我使用 Github 来托管我的网站，下面是我引用的文档/博客列表:

* https://hongtaoh.com/en/2021/04/05/hugo-deploy-github-actions/
* https://gohugo.io/hosting-and-deployment/hosting-on-github/
* https://levelup.gitconnected.com/build-a-personal-website-with-github-pages-and-hugo-6c68592204c7
* https://www.pluralsight.com/guides/how-to-host-your-static-webpages-on-github-pages

## 4. 其他细节

### 评论
为了设置 Utterances 评论部分，我更新了 ```config.toml``` 并将 Utterances 应用程序安装到 repo。还有其他 [alternatives](https://gohugo.io/content-management/comments/) 类似的 disqus 和 valine。

### GDOCS 简码
感谢 [Ashish Tiwari 的 Shortcodes post ](https://ashish.one/gist/add-responsive-google-slides-on-hugo/) 和 [Wowchemy-Hugo-Modules ](https://github.com/linozen/wowchemy-hugo-modules)，我能够加入 GDOCS 的 Shortcodes 功能。特别是，要注意你的简码。
```code
{{</*gdocs src="???"*/>}}
```
，```src```URL 应该是发布到 Web 的 URL（在你的 Google 幻灯片中，转到文件，然后发布到 Web，选择链接或嵌入并复制 src="？？？”），而不是共享的 URL。我纠正了这一点，因为我发现只有我的笔记本电脑网络可以显示 GDOCS（而且显示内容不是很令人满意），而 iPad 和 iPhone 不能。特别感谢 [Cecina Babich Morrow 的帖子](https://babichmorrowc.github.io/post/add-google-doc/)。
