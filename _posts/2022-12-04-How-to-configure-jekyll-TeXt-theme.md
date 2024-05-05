---
title: "How to configure jekyll-TeXt theme and deploy it on github pages"
tags:
- jekyll
- jekyll theme
---

<h3 style="text-align: center;">
  In this article, you will learn how to install the theme, setup your site, local preview for development, build and publish.
</h3>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

> This jekyll theme was created by [@kitian616](https://github.com/kitian616), Thank you for making it better.

## How do themes work?
Jekyll themes allow you to contain all the templating and presentational code within a Ruby gem, much in the same way Jekyll plugins are contained. This means the design can be easily applied to a site, used on multiple sites, and the site codebase isn’t cluttered by the presentational layer.
By nature, Any well structured site that has easily editable content is ‘themeable’ — a layer, or skin, That presents content in the way the owner or creator intended; Jekyll is no different. Pages, posts and any other form of formatted content can be segregated from the templating files.

```
├── 404.html
├── Gemfile
├── _config.yml
├── _data
│   └── locale.yml
├── _posts
│   └── ...
├── about.md
├── archive.html
└── index.html
```

<em style="text-align: center;">
  Example of a Jekyll site structure when using a theme gem
</em>

## Installing the Theme

### Common Method
To install it with common method, All you need to do is copying all the theme files to your project. There are several ways to do so:

* Clone [jekyll-TeXt-theme](https://github.com/kitian616/jekyll-TeXt-theme) from github.
* Or download and unzip the [file](https://github.com/kitian616/jekyll-TeXt-theme/archive/master.zip) to your Jekyll site directory.
* If you host your site on GitHub Pages, you can just fork [jekyll-TeXt-theme](https://github.com/kitian616/jekyll-TeXt-theme), then rename the repository to USERNAME.github.io — replacing USERNAME with your GitHub username.

![Image by @kitian616](https://raw.githubusercontent.com/kitian616/jekyll-TeXt-theme/master/docs/assets/images/github-fork.jpg)

![Image by @kitian616](https://raw.githubusercontent.com/kitian616/jekyll-TeXt-theme/master/docs/assets/images/github-rename-repo.jpg)

<h1 style="text-align: center;">
  Comming soon...
</h1>

