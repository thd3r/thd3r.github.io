---
title: Customize Chirpy Jekyll Theme & deploy it on Github Pages
date: 2022-03-27 14:29:00
mermaid: true
categories: [Theme, Chirpy Jekyll Theme]
tags: [theme, chirpy jekyll theme, jekyll, jekyll theme]
image:
    path: https://camo.githubusercontent.com/7deb9e4905ab1e73cec83fa80f3a5d0c7f613e6b522a9fdc41d5c79fad37eda8/68747470733a2f2f6368697270792d696d672e6e65746c6966792e6170702f636f6d6d6f6e732f646576696365732d6d6f636b75702e706e67
---

This theme customization is not much to configure and you can get this theme in this [repository](https://github.com/cotes2020/jekyll-theme-chirpy/tree/master). This theme project is developed by talented developers especially with knowledge of ruby ​​and also jekyll

So lets break down the different components:

* [Ruby](https://www.ruby-lang.org/en/) is a dynamic, object-oriented programming language known for its simplicity and readability. It is often used for web development, particularly with the Ruby on Rails framework.

* [Gems](https://rubygems.org/) are pre-packaged libraries or modules in Ruby that add functionality to applications. They can be easily installed and managed using the RubyGems package manager, enabling developers to quickly integrate features without having to reinvent the wheel.

* [Jekyll](https://jekyllrb.com/) is a static site generator that transforms plain text into beautiful static websites and blogs, and is the foundation of our “blog-as-code” approach. Turning the [markdown](https://www.markdownguide.org/) files we use to write articles, into webpages like you’re reading now.

* [Chirpy](https://chirpy.cotes.page/) an awesome text-focused theme for Jekyll created by [Cotes Chung](https://github.com/cotes2020). Or more specifically his amazing [Chirpy Starter template](https://github.com/cotes2020/chirpy-starter) that automates the creation and updates of our site going forward using [GitHub Actions](https://docs.github.com/en/actions) our first foray into CI/CD using GitHub.

* [Github Pages](https://pages.github.com/) and an underlying Github repo will be use to store and host everything related to our site.

# Setup Ruby, Gem and Jekyll

## Install Ruby and other prerequisites

```terminal
thd3r@425:~/github$ sudo apt-get install ruby-full build-essential zlib1g-dev
[sudo] password for thd3r:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
build-essential is already the newest version (12.9ubuntu3).
zlib1g-dev is already the newest version (1:1.2.11.dfsg-2ubuntu9.2).
The following additional packages will be installed:
  ri
The following NEW packages will be installed:
  ri ruby-full
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 6788 B of archives.
After this operation, 38.9 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu jammy/universe amd64 ri all 1:3.0~exp1 [4206 B]
Get:2 http://archive.ubuntu.com/ubuntu jammy/universe amd64 ruby-full all 1:3.0~exp1 [2582 B]
Fetched 6788 B in 1s (4970 B/s)
Selecting previously unselected package ri.
(Reading database ... 47201 files and directories currently installed.)
Preparing to unpack .../ri_1%3a3.0~exp1_all.deb ...
Unpacking ri (1:3.0~exp1) ...
Selecting previously unselected package ruby-full.
Preparing to unpack .../ruby-full_1%3a3.0~exp1_all.deb ...
Unpacking ruby-full (1:3.0~exp1) ...
Setting up ri (1:3.0~exp1) ...
Setting up ruby-full (1:3.0~exp1) ...
```

### Add environment variables to your ~/.bashrc file

```sh
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## Install Jekyll and Bundler

```sh
gem install jekyll bundler
```

# Getting Started

## Select your option to get started

### Using the Starter (Recommended)

This approach simplifies upgrades, isolates unnecessary files, and is perfect for users who want to focus on writing with minimal configuration.

1. Sign in to GitHub and navigate to the [**starter**][starter].
2. Click the <kbd>Use this template</kbd> button and then select <kbd>Create a new repository</kbd>.
3. Name the new repository `<username>.github.io`, replacing `username` with your lowercase GitHub username.

### Forking the Theme

This approach is convenient for modifying features or UI design, but presents challenges during upgrades. So don't try this unless you are familiar with Jekyll and plan to heavily modify this theme.

1. Sign in to GitHub.
2. [Fork the theme repository](https://github.com/cotes2020/jekyll-theme-chirpy/fork).
3. Name the new repository `<username>.github.io`, replacing `username` with your lowercase GitHub username.

## Installing dependencies of chirpy-starter 

This requires some GEM's to be installed before it can be used. On your local development machine, clone the new repo and go to the repo root directory and run `bundle` command

```sh
bundle
```

## Verify the site locally and view the changes in browser

Run this command to see the changes that have been made

```sh
bundle exec jekyll serve -H 0.0.0.0 -t
```

# Configure

## Configuration file table data

There are several configuration files that we can modify to make changes to the site.

| File                 | Details             |
| :------------------- | :--------------- |
| /_config.yml         | The main configuration file for our Chirpy theme’d Jekyll site |
| /_data/contact.yml   | Manages the contact options displayed at the bottom of the sidebar |
| /_data/share.yml     | Manages what platforms visitors can share our articles to |
| /_posts              | Manage your posts with the file format **YYYY-MM-DD-TITLE.EXTENSION** note that the EXTENSION must be one of **md** and **markdown** |
| /_tabs               | Contains the menu configuration file in the sidebar |
| /assets/img/favicons | Customize the Favicon |

## Configuring the _config.yaml

These are the things you can change

| Key            | Details    |
| :------------- | :----------|
| lang           | The language of your site (e.g., en, es) |
| timezone       | Your local timezone | 
| title          | The title of your site |
| tagline        | It will display as the subtitle |
| description    | Used by seo meta and the atom feed |
| url            | The base URL of your site (e.g., https://yourdomain.com). |
| avatar         | The URL of your profile picture |
| author         | Your name or pen name |
| social         | Social media links and names for them |

## Configuring the Favicon

The [favicons](https://www.favicon-generator.org/about/) of [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/) are placed in the directory **assets/img/favicons/** You may want to replace them with your own. The following sections will guide you to create and replace the default favicons and If your Jekyll site doesn’t have this **assets/img/favicons/** directory yet, Just create one.

To make this whole process easier we are going to use this handy tool [Real Favicon Generator](https://realfavicongenerator.net/) to create all the required files.

![Real Favicon Generator](/assets/img/writeup/2022-03-27/Screenshot_2025-03-27_16-21-57.png)
_Create your Favicons using Real Favicon Generator_

1. Click <kbd>Pick your favicon image</kbd> to upload your image
2. Scroll to the bottom of the page and click <kbd>Next</kbd>
3. Click <kbd>Download</kbd> to download the generated favicons
4. Extract the contents of the download, and remove the following files
  * browserconfig.xml
  * site.webmanifest
5. Upload the remaining files to our GitHub repo to replace the original files in the direcotry **assets/img/favicons/**

## Configure to Deploy the Website

### Enable Github Pages

The Github Action so Jekyll can automatically generate the static site content that Github Pages will then present our visitors.

1. Open our Github Repo `Settings`
2. Select `Pages` from the settings page
3. Change the Build and Deploy `Source` to `Github Actions`

Now when we commit changes to our repository, the Github Action will automatically run and re-generate our site content. If the action fails for any reason you can check out the logs under the Actions tab in your Github repository.

### Commit and push changes

After we have made changes and configured files here and there, It is time to publish the changes to the repository so that the changes can be accessed by the public. Run the following command and make sure you are authenticated.

* This command will display what we have changed.

```sh
git status
```

* Add all the changes that have been made

```sh
git add --all
```

* Make a commit

```sh
git commit -m "Initial commit"
```

* Execution of changes

```sh
git push -u origin main
```

## Conclusion

So far we have done a lot starting from setting up the theme requirements, configuring some important files, customizing the favicon and deploying the site. We also learned how to use git commands, learned a little about Ruby, Bundle and Jekyll.