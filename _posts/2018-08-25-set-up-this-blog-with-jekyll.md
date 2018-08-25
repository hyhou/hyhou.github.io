---
layout: default
title: "Setup this blog with jekyll on github pages"
tags: [other]
---

# Setup this blog with jekyll on github pages

I rarely touched web related stuff before, but I do know that github have [Github Pages](https://pages.github.com/). I think it could be a good place to record my projects. So here is how I setup the blog from knowing nothing with github pages and jekyll.

## Make space for your page

The github page is hosted in the repo and there are two ways.

### master branch
In this way, you host the page on the master branch of a repo(likely be a new one). 

- Following the instruction on [Github Pages](https://pages.github.com/), create a new repo. (eg: yourusername.github.io) 

### gh-pages branch
In this way, you host the page on the gh-pages branch of an already existed project.

## Choose a jekyll theme
So now there are nothing in your repo except a readme probably. You may already notice the keyword jekyll and theme. 
Jekyll is a static site generator used by Github to process the content you uploaded to repo. With jekyll as the engine of github pages, the ideal scene should be you just upload markdown content and Github automatically process your content and generate a html page for your content based on the theme you selected.

But apparently it really confuses me while I notice there is a huge gap between an empty repo and the scene while I just write, upload and enjoy my beautiful blog.

Okay then, let's back to the work.

There are many people developing themes for jekyll and Github offcially supports several that you can directly select in the settings of your project.

You can find detailed steps here: 
- [About Jekyll themes on GitHub](https://help.github.com/articles/about-jekyll-themes-on-github/)
- [Adding a Jekyll theme to your GitHub Pages site](https://help.github.com/articles/adding-a-jekyll-theme-to-your-github-pages-site/)

But for simple steps:
- Click the setting of your repo.
- In the GitHub Pages section -> Theme Chooser -> Change theme
- In the poped page, select the one you like.
- Go back to your repo, you will notice you have two new files **_config.yml** and **index.md**
- now access yourusername.github.io and you will see the content of index.md showing in the theme you selected.

## Uploading post
Okay, now we seems closer to the ideal scene. We have an index now, then how should we write normal post?
According to the [Writting posts](https://jekyllrb.com/docs/posts/) from Jekyll website:
- First, we need create a folder named **_posts**.
- We create new posts under this **_posts** folder.
- The new posts should be named following : yyyy-mm-dd-title.md(the file extension is up to you) format.
- And do not forget the paramters for jekyll to process your content with the theme (So called front matter)

For example, a file named: *2011-12-31-new-years-eve-is-awesome.md* with content:
```
---
layout: post
title:  "Welcome to Jekyll!"
date:   2015-11-17 16:16:01 -0600
categories: jekyll update
---

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `bundle exec jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.
```
Content between **- - -** is what we said about **front matter**.
The **- - -** will trigger the jekyll engine to process the content with the theme, and the layout tells the engine which "html jacket" the content need.
You may need to change the **layout:post** to **layout:default** as your theme may only have one "jacket" for all content.

## List your post
So once you upload your content, you may notice that you do not know what's the address for that post and that's really bad, you need a way to list the posts and navigate through. Here describes several method, [Writting posts](https://jekyllrb.com/docs/posts/). I think the tag way is easier:
```
---
layout: post
title:  "Welcome to Jekyll!"
date:   2015-11-17 16:16:01 -0600
tags: [test]
---

```
After you specify what tag your post have, you could list all the posts with a specific tag in your **index** page or any other page like this:
{% raw %}
```
<ul>
  {% for post in site.tags["test"]%}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
```
{% endraw %}