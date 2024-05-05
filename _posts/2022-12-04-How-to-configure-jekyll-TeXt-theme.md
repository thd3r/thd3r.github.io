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

<h1 style="text-align: center;">
  Quick Start
</h1>

## Installing the Theme

### Common Method
To install it with common method, All you need to do is copying all the theme files to your project. There are several ways to do so:

* Clone [jekyll-TeXt-theme](https://github.com/kitian616/jekyll-TeXt-theme) from github.
* Or download and unzip the [file](https://github.com/kitian616/jekyll-TeXt-theme/archive/master.zip) to your Jekyll site directory.
* If you host your site on GitHub Pages, you can just fork [jekyll-TeXt-theme](https://github.com/kitian616/jekyll-TeXt-theme), then rename the repository to USERNAME.github.io — replacing USERNAME with your GitHub username.

![Image by @kitian616](https://raw.githubusercontent.com/kitian616/jekyll-TeXt-theme/master/docs/assets/images/github-fork.jpg)

![Image by @kitian616](https://raw.githubusercontent.com/kitian616/jekyll-TeXt-theme/master/docs/assets/images/github-rename-repo.jpg)

### Ruby Gem Method
* Add this line to your Jekyll site’s **Gemfile**:
```
gem "jekyll-text-theme"
```
* Add this line to your Jekyll site’s **_config.yml** file:
```
theme: jekyll-text-theme
```

<h1 style="text-align: center;">
  Customization
</h1>

## Configuration
Jekyll allows you to concoct your sites in any way you can dream up, and it’s thanks to the powerful and flexible configuration options that this is possible. These options can either be specified in a **_config.yml** file placed in your site’s root directory, Or can be specified as flags for the jekyll executable in the terminal.

> For technical reasons, _config.yml is NOT reloaded automatically when you use jekyll serve. If you change this file, please restart the server process.

## Site Settings
### Theme
If you’re using the Ruby gem version of the theme you’ll need this line to activate it:
```
theme: jekyll-text-theme
```

### Skin
```
text_skin: default # "default" (default), "dark", "forest", "ocean", "chocolate", "orange"
```

### Highlight Theme
```
highlight_theme: default # "default" (default), "tomorrow", "tomorrow-night", "tomorrow-night-eighties", "tomorrow-night-blue", "tomorrow-night-bright"
```

### URL
The base hostname and protocol for your site. if you are hosting the site on Github Pages this will be set as the GitHub Pages domain (cname or user domain). For example, https://thd3r.github.io or https://domain.name if there is cname file.

> Jekyll 3.3 overrides this value with url: http://localhost:4000 when running jekyll serve in a development environment2. You can specifying Jekyll environment3 to production environment by JEKYLL_ENV=production to avoid this behavior.

### Base URL
The base URL for your site, default to ‘/’. If you are hosting the site on Github Pages this will be set as the project name for project pages if none is set1.

### Title
The name of your site.
```
title: "My Awesome Website"
```

### Description
Use some words to describe your site.
```
description: > # this means to ignore newlines until "nav_lists:"
  A website with awesome stories.
```

## Language and Timezone
### Language
The language of your site, you can override it with different ones on specific posts, pages by YAML Front Matter4, learn more at Internationalization.
```
lang: en
```

### Timezone
Set the time zone for site generation. This sets the TZ environment variable, which Ruby uses to handle time and date creation and manipulation. A list of all available values can be found HERE.

When serving on a local machine, the default time zone is set by your operating system. But when served on a remote host/server, the default time zone depends on the server’s setting or location.5
```
timezone: Asia/Shanghai
```

## Author and Social
Information of the site author (a person, a team or an organization).

### Type
Type of the site author, a person or an organization, used by [schema.org](https://schema.org/) markup, default as “person”.

### Name
Used to assign a site author.

### Avatar
Photo or Logo for site author

### Bio
Short introduction for site author

### Social
Username or id of site author’s social networks.

TeXt supports Email, Facebook, Twitter, Weibo, Google Plus, Telegram, Medium, Zhihu, Douban, Linkedin, Github and Npm, more to be added.

Depending on your settings, the social network buttons would show on every pages’ footer.

## GitHub repository
Setting for [GitHub Metadata](https://github.com/jekyll/github-metadata) plugin, you can refer to [HERE](https://github.com/jekyll/github-metadata/blob/master/docs/configuration.md#configuration) for more info.

In order for jekyll-github-metadata to know what metadata to fetch it must be able to determine the repository NWO to ask GitHub about.

“NWO” stands for “name with owner.” It is GitHub lingo for the username of the owner of the repository plus a forward slash plus the name of the repository, e.g. kitian616/jekyll-TeXt-theme, where “kitian616” is the owner and “jekyll-TeXt-theme” is the repository name.
```
repository: user_name/repo_name
```









**This article is part of [HERE](https://kitian616.github.io/jekyll-TeXt-theme/docs/en/quick-start)**

<h1 style="text-align: center;">
  Comming soon...
</h1>

