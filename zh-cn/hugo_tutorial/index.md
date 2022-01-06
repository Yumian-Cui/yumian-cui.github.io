# Hugo网站搭建经验帖


<!--more-->
<!-- ![](/images/Hugo-Logo.png "A blog that shares some of my own experiences with building Hugo website.") -->

## 1. Requirements

1. install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. install [hugo](https://gohugo.io/getting-started/quick-start/)

## 2. Get started

I would suggest look over official documentations for basic installation and configuration. If you cannot solve problem by then, check out blog posts that might be helpful. 

### docs

* https://gohugo.io/getting-started/quick-start/
* https://hugoloveit.com/ (this is the LoveIt theme in Hugo, but format&troubleshoot should generalize to other templates)
* [YouTube tutorial step by step](https://www.youtube.com/watch?v=5GnFZ8XpMak)

### blogs

* [is-there-a-place-we-can-put-non-blog-files-pdf-files-in-blogdown](https://community.rstudio.com/t/is-there-a-place-we-can-put-non-blog-files-pdf-files-in-blogdown/10138/3)
* [how-to-make-a-mulilingual-website-with-hugo](https://yonkov.github.io/post/how-to-make-a-mulilingual-website-with-hugo/)

### misc

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

## 3. Publish your page

Publishing the page is a bit of hassle for me. My sincere suggestion after this experience is to find a tutorial and closely follow the steps. Even if you don't like the theme or the tutorial style, it's always easier to build up your understanding first and level up/optimize from there.

I used GitHub to host my website and here is a list of docs/blogs that I referred to:

* https://hongtaoh.com/en/2021/04/05/hugo-deploy-github-actions/
* https://gohugo.io/hosting-and-deployment/hosting-on-github/
* https://levelup.gitconnected.com/build-a-personal-website-with-github-pages-and-hugo-6c68592204c7
* https://www.pluralsight.com/guides/how-to-host-your-static-webpages-on-github-pages

## 4. Other details

### comment
To set up utterances comment section, I updated both ```config.toml``` and installed utterances app to repo. There are other [alternatives](https://gohugo.io/content-management/comments/) like Disqus and Valine. 

### gdocs shortcodes
Thanks to [Ashish Tiwari's shortcodes post](https://ashish.one/gist/add-responsive-google-slides-on-hugo/) and [wowchemy-hugo-modules](https://github.com/linozen/wowchemy-hugo-modules), I'm able to incorporate the gdocs shortcodes functionality. In particular, be aware in your shortcodes 
```code
{{</*gdocs src="???"*/>}}
```
, the ```src``` url should be the one published to web (in your google slides, go to **File** and then **Publish to the web**, select either link or embed and copy the url in src="???"), not the shared url. I corrected this once I found only my laptop web can show gdocs (also the display is not very satisfactory) while ipad and iphone can't. Specifial thanks to [Cecina Babich Morrow's post](https://babichmorrowc.github.io/post/add-google-doc/).
