---
title: "Transform Your Website with the Chirpy Jekyll Theme: A Step-by-Step Guide to Customization and Deployment on GitHub Pages"
date: 2022-03-27 14:29:00
mermaid: true
categories: [Technology & Tutorials]
tags: [theme, chirpy jekyll theme, jekyll, jekyll theme]
image:
    path: https://camo.githubusercontent.com/7deb9e4905ab1e73cec83fa80f3a5d0c7f613e6b522a9fdc41d5c79fad37eda8/68747470733a2f2f6368697270792d696d672e6e65746c6966792e6170702f636f6d6d6f6e732f646576696365732d6d6f636b75702e706e67
    alt: Responsive rendering of Chirpy theme on multiple devices.
---

Jekyll is a powerful static site generator that, when combined with GitHub Pages, allows you to easily host and manage blogs and websites. If you want a clean, minimalist, and customizable theme, the Chirpy Jekyll theme is an excellent choice. This theme customization is not much to configure and you can get this theme in this [repository](https://github.com/cotes2020/jekyll-theme-chirpy/tree/master). This theme project is developed by talented developers especially with knowledge of Ruby ​​and also Jekyll. In this guide, we’ll walk you through the steps to customize the Chirpy theme and deploy it on GitHub Pages.

So lets break down the different components:

* [Ruby](https://www.ruby-lang.org/en/) is a dynamic, object-oriented programming language known for its simplicity and readability. It is often used for web development, particularly with the Ruby on Rails framework.

* [Gems](https://rubygems.org/) are pre-packaged libraries or modules in Ruby that add functionality to applications. They can be easily installed and managed using the RubyGems package manager, enabling developers to quickly integrate features without having to reinvent the wheel.

* [Jekyll](https://jekyllrb.com/) is a static site generator that transforms plain text into beautiful static websites and blogs, and is the foundation of our “blog-as-code” approach. Turning the [markdown](https://www.markdownguide.org/) files we use to write articles, into webpages like you’re reading now.

* [Chirpy](https://chirpy.cotes.page/) an awesome text-focused theme for Jekyll created by [Cotes Chung](https://github.com/cotes2020). Or more specifically his amazing [Chirpy Starter template](https://github.com/cotes2020/chirpy-starter) that automates the creation and updates of our site going forward using [GitHub Actions](https://docs.github.com/en/actions) our first foray into CI/CD using GitHub.

* [Github Pages](https://pages.github.com/) and an underlying Github repo will be use to store and host everything related to our site.

# Step-by-Step Guide

## Setting Up the Environment

Before you start, ensure Ruby, Bundler, and Jekyll are installed. Use the following commands to install dependencies

```sh
sudo apt-get install ruby-full build-essential zlib1g-dev
gem install jekyll bundler
```

## Set up environment variables to manage Ruby gems efficiently

```sh
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## Select your option to get started

### Using the Starter (Recommended)

This approach simplifies upgrades, isolates unnecessary files, and is perfect for users who want to focus on writing with minimal configuration.

1. Sign in to GitHub and navigate to the [chirpy-starter](https://github.com/cotes2020/chirpy-starter)
2. Click the <kbd>Use this template</kbd> button and then select <kbd>Create a new repository</kbd>
3. Name the new repository `<username>.github.io`, replacing `username` with your lowercase GitHub username

### Forking the Theme

This approach is convenient for modifying features or UI design, but presents challenges during upgrades. So don't try this unless you are familiar with Jekyll and plan to heavily modify this theme.

1. Sign in to GitHub.
2. [Fork the theme repository](https://github.com/cotes2020/jekyll-theme-chirpy/fork).
3. Name the new repository `<username>.github.io`, replacing `username` with your lowercase GitHub username.

## Installing dependencies of chirpy-starter 

This requires some GEM's to be installed before it can be used. On your local development machine, Once you’ve set up the repository, run `bundle` in the root directory to install all necessary dependencies

```sh
bundle
```

## Running the Site Locally

To verify the site looks good locally, use the following command:

```sh
bundle exec jekyll serve
```

# Configure

Now it’s time to make the site your own. Modify the `_config.yml` file to set the language, title, tagline, social links, and more. Don’t forget to replace the default favicon in the `assets/img/favicons/` directory with your own, using a tool like Real [Real Favicon Generator](https://realfavicongenerator.net/)

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

The [Favicons](https://www.favicon-generator.org/about/) of [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/) are placed in the directory **assets/img/favicons/** You may want to replace them with your own. The following sections will guide you to create and replace the default favicons and If your Jekyll site doesn’t have this **assets/img/favicons/** directory yet, Just create one.

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

To deploy the website, enable GitHub Pages in the repository settings. GitHub Actions will automatically build your site and host it for free.

### Enable Github Pages

The Github Action so Jekyll can automatically generate the static site content that Github Pages will then present our visitors.

1. Open our Github Repo `Settings`
2. Select `Pages` from the settings page
3. Change the Build and Deploy `Source` to `Github Actions`

Now when we commit changes to our repository, the Github Action will automatically run and re-generate our site content. If the action fails for any reason you can check out the logs under the Actions tab in your Github repository.

### Commit and push changes

After we have made changes and configured files here and there, It is time to publish the changes to the repository so that the changes can be accessed by the public. Run the following command and make sure you are authenticated.

This command will display what we have changed.

```sh
git status
```

Add all the changes that have been made

```sh
git add --all
```

Make a commit

```sh
git commit -m "Initial commit"
```

Execution of changes

```sh
git push -u origin {BRANCH_NAME}
```

## Conclusion

By following these simple steps, you can easily set up, customize, and deploy a stylish Jekyll site with the Chirpy theme. Whether you’re building a blog or a personal website, Chirpy offers a clean and efficient way to get online.
