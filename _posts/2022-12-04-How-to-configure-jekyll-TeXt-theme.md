---
title: "How to configure jekyll-TeXt theme and deploy it on github pages"
tags:
- jekyll
- jekyll theme
- jekyll-TeXt-theme
---

<h3 style="text-align: center;">
  In this article, you will learn how to install the theme, setup your site, local preview for development, build and publish.
</h3>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

<h1 style="text-align: center;">
  Overview
</h1>

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

Example of a Jekyll site structure when using a theme gem

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
<cite style="text-align: center">
  source: <a href="https://raw.githubusercontent.com/kitian616/jekyll-TeXt-theme/master/docs/assets/images/github-fork.jpg">github-fork.jpg</a>
</cite>

![Image by @kitian616](https://raw.githubusercontent.com/kitian616/jekyll-TeXt-theme/master/docs/assets/images/github-rename-repo.jpg)
<cite style="text-align: center">
  source: <a href="https://raw.githubusercontent.com/kitian616/jekyll-TeXt-theme/master/docs/assets/images/github-rename-repo.jpg">github-rename-repo.jpg</a>
</cite>

### Ruby Gem Method
* Add this line to your Jekyll site’s **Gemfile**:

```
gem "jekyll-text-theme"
```

* Add this line to your Jekyll site’s **_config.yml** file:

```
theme: jekyll-text-theme
```

## Local Preview
Run **bundle exec jekyll serve** to start the development server, Then you can visit http://localhost:4000/ to preview your site.

<h1 style="text-align: center;">
  Customization
</h1>

In this chapter we will learn how to configure several files in the form of yml, css, html formats where we will change, add and delete and also we will learn how to upload a logo and add a favicon. We will arrange everything necessary in this chapter

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
Set the time zone for site generation. This sets the TZ environment variable, which Ruby uses to handle time and date creation and manipulation. A list of all available values can be found [HERE](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

When serving on a local machine, the default time zone is set by your operating system. But when served on a remote host/server, the default time zone depends on the server’s setting or location.

```
timezone: Asia/City
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

Depending on your settings, the social network buttons would show on every pages footer.

## GitHub repository
Setting for [GitHub Metadata](https://github.com/jekyll/github-metadata) plugin, you can refer to [HERE](https://github.com/jekyll/github-metadata/blob/master/docs/configuration.md#configuration) for more info.

In order for jekyll-github-metadata to know what metadata to fetch it must be able to determine the repository NWO to ask GitHub about.

“NWO” stands for “name with owner.” It is GitHub lingo for the username of the owner of the repository plus a forward slash plus the name of the repository, e.g. kitian616/jekyll-TeXt-theme, where “kitian616” is the owner and “jekyll-TeXt-theme” is the repository name.

```
repository: user_name/repo_name
```

## Setting the _button.scss

### This file is located in **_sass/common/components/**
![IMAGE-1](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/button/image1.png)

### Some functions will have their values changed
![IMAGE-2](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/button/image2.png)

![IMAGE-3](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/button/image3.png)

## Setting the _dark.scss

### This file is located in **_sass/skins/**

**Why dark.scss?** because in the _config.yml configuration file in the **text_skin:** section I chose **dark**

### The image below will explain some of the functions in the _dark.scss file
![IMAGE-1](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/skins/image1.png)

### In the **$select-color** function section on line 50 change **$main-color-1** to **#fff**
![IMAGE-2](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/skins/image2.png)

## Setting the _variables.scss 

### This file is located in **_sass/common/**
In the **_variables.scss** file you can modify the font and add external fonts

### Modify and add external fonts
I will modify the font and add the font via external path and I use the font **FiraCode-Regular.ttf**

![IMAGE-1](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/variable/image1.png)

To add external fonts you must add **some-font.ttf** in the root folder

## Setting the locale.yml and footer.html

### This file is located in **_data/** and **_includes/**
Both files configure copyright so here we will modify copyright through those two files

### Modify the locale.yml 

```
// Before
COPYRIGHT_DATES         : "2021"
// After
COPYRIGHT_DATES         : "Change to current year"
```

### Modify the footer.html 
![image-1](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/image1.png)

## Setting the variables.yml 

### This file is located in **_data/**
This configuration file contains settings about the page

### Modify the variables.yml
In this configuration file I will allow **readmore** and disable **comments**

```
// Before
show_readmore: false
// After
show_readmore: true

// Before
comment: true
// After
comment: false
```

## Setting the article-footer.html and articles.html

### This file is located in **_includes/** and **_layouts/**
These two files contain the configuration for the article

### Modify the article-footer.html 
I will remove features that I think are not very useful for me but if you need them then leave it like that

![image-2](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/image2.png)

### Modify the articles.html 

```
// Add
articles:
  data_source: site.sample_page
  show_excerpt: true
  show_readmore: true
  show_info: true
```

## Setting the home.html

### This file is located in **_layouts/**
This file is part of the page configuration

###  Modify the home.html
I will make changes to line 31

```
// Before
show_cover: false
// After
show_cover: true
```

## Setting the _text.scss

### This file is located in **_sass/common/classes/**
This CSS file contains configuration regarding text color settings

### Modify the _text.scss
I will make changes to line 27

```
a:not(.button) {
    // Before
    @include link-colors($text-color-theme-dark, $main-color-1);
    // After
    @include link-colors($text-color-theme-dark, #fff);
  }
}
```

## Setting the _article-content.scss

### This file is located in **_sass/components/**
This CSS file contains configuration regarding article content settings

### Modify the _article-content.scss
I will add this function in the final line

```
 img:not(.emoji) {
    display: block; /* Ensures images are centered properly */
    margin: 0 auto; /* Centers images horizontally */
  }
```

## Setting the _author-links.scss

### This file is located in **_sass/components/**
This CSS file contains configuration regarding author link color settings where you can change the text color and icon color in this file

### Some functions will have their values changed
![IMAGE-AUTHOR-LINKS](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/author-links/image1.png)

## Setting the _footer.scss

### This file is located in **_sass/components/**
This CSS file contains footer settings

### Modify the _footer.scss 
I will make changes to line 10

```
a {
    // Before
    @include link-colors ($footer-text-color, $main-color-1);
    // After
    @include link-colors ($footer-text-color, $main-color-3);
  }
```

## Setting the _header.scss

### This file is located in **_sass/components/**
This CSS file contains header settings

### Modify the _header.scss
I will make changes to line 16

![image-3](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/image3.png)

## Setting the _tags.scss

### This file is located in **_sass/components/**
This CSS file contains page tags settings

### Modify the _tags.scss 
![image-4](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/image4.png)

## Setup Your Logo
This time we will upload a logo and add a favicon

> A favicon, short for “favorite icon,” is a small icon associated with a particular website or web page. It is a file containing one or more small icons that are used to represent the website or web page in various contexts

### Add Logo
In the **_includes/svg/** folder delete the default **logo.svg** and add your logo

### Add favicon.ico
We can add **favicon.ico** file in root path and **assets/** path

### Setting the favicon.html
This file is located in **_includes/head/**

### Modify the favicon.html 

```
<link rel="apple-touch-icon" sizes="180x180" href="assets/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="assets/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="assets/favicon-16x16.png">
<link rel="manifest" href="assets/site.webmanifest">
<link rel="mask-icon" href="assets/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">
```

### Delete the following image
The following image is in the **assets/** path
* android-chrome-192x192.png
* mstile-150x150.png
* apple-touch-icon.png
* favicon-32x32.png
* favicon-16x16.png

### Add necessary images
After we delete the image above, now we will add an image but in the format described in the image above, simply change the image files but leave the name unchanged.

### Create the site.webmanifest
Create a site.webmanifest file in the **assets/** path with the following contents

```
{
    "name": "TeXt Theme",
    "short_name": "TeXt Theme",
    "icons": [
        {
            "src": "android-chrome-192x192.png",
            "sizes": "192x192",
            "type": "image/png"
        }
    ],
    "theme_color": "#ffffff",
    "background_color": "#ffffff",
    "display": "standalone"
}
```

### Create the browserconfig.xml
Create a browserconfig.xml file in the **assets/** path with the following contents

```
<?xml version="1.0" encoding="utf-8"?>
<browserconfig>
    <msapplication>
        <tile>
            <square150x150logo src="mstile-150x150.png"/>
            <TileColor>#b91d47</TileColor>
        </tile>
    </msapplication>
</browserconfig>
```

<h1 style="text-align: center;">
  Deploy it on github pages
</h1>

This time we will share what we have done previously to the github page. In this chapter we will also learn to use git commands.

> Git is a very popular version control system used by software developers to manage changes in their source code. This enables development teams to work collaboratively on software projects safely and efficiently.

## Deploying
Before deploying we have to make sure that we are in that Git repository. When we are in the repository the next step is to create a **dev** branch

Use the following command to create a new branch and deploy it

```
// Create a new branch
git checkout -b dev
// deploy it
git add *
git commit -m "setup web"
git status 
git push -u origin dev
```

### After running the command above go to your repository and you will see this information just click **Compare and pull request**

![image-5](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/image5.png)

### Create pull request
![image-6](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/image6.png)

### Merge pull request
![image-7](https://raw.githubusercontent.com/thd3r/thd3r.github.io/dev/assets/images/writeup/2022-12-04-How-to-configure-jekyll-TeXt-theme/content/images/image7.png)


## Credit

Credit [@kitian616](https://github.com/kitian616), Thank you for making it better.

## Conclusion

In this article we learn how to configure several files, upload a logo, add a favicon and also deploy it to a github page

If there is a word or sentence error in this article, Please let me know [HERE](https://twitter.com/thd3r_)
