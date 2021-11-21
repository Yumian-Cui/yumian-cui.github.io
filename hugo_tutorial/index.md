# Build your Hugo website

<!--more-->
<!-- ![](/images/Hugo-Logo.png "A blog that shares some of my own experiences with building Hugo website.") -->

## 1. Requirements

1. install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. install [hugo](https://gohugo.io/getting-started/quick-start/)

## 2. Get started

I would suggest look over official documentations for basic installation and configuration. If you cannot solve problem by then, check out blog posts that might be helpful. 

**Docs:**

* https://gohugo.io/getting-started/quick-start/
* https://hugoloveit.com/ (this is the LoveIt theme in Hugo, but format&troubleshoot should generalize to other templates)
* [YouTube tutorial step by step](https://www.youtube.com/watch?v=5GnFZ8XpMak)

**Blogs:**

* [is-there-a-place-we-can-put-non-blog-files-pdf-files-in-blogdown](https://community.rstudio.com/t/is-there-a-place-we-can-put-non-blog-files-pdf-files-in-blogdown/10138/3)
* [how-to-make-a-mulilingual-website-with-hugo](https://yonkov.github.io/post/how-to-make-a-mulilingual-website-with-hugo/)

**Misc:**

* [Font_Awesome.docset (icons)](https://kapeli.com/cheat_sheets/Font_Awesome.docset/Contents/Resources/Documents/index)

{{< admonition note "Common Issues" >}}
* If your page under development mode crashed, be patient and maybe reload the server in terminal with ```Ctrl-C``` and ```hugo server -D```
* Be careful about syntax, format, especially with multilingual setting. 
* If you're not sure the organization, always refer to the **themes/xxx(LoveIt)/exampleSite** folder first that's contained in every Hugo repo after you clone it.
* When you want to add the featured image for the content preview in the home page, do:
  ``` Markdown
  resources:
  - name: "featured-image"
    src: "featured-image.png" 
  ```
  and name your md file to be ```index.md```. Don't forget to add the ```<!--more-->``` divider if you want to tell Hugo only summarizes the content before divider in preview. 
{{< /admonition >}}






