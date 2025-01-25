---
{"dg-publish":true,"permalink":"/software/hugo/hugo-quick-start/","title":"Quick start","tags":["clippings","hugo","linux"]}
---

In this tutorial you will:

1. Create a site
2. Add content
3. Configure the site
4. Publish the site

## Prerequisites

Before you begin this tutorial you must:

1. [Install Hugo](https://gohugo.io/installation/) (extended or extended/deploy edition, v0.128.0 or later)
2. [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

You must also be comfortable working from the command line.

## Create a site
### Commands

Verify that you have installed Hugo v0.128.0 or later.

Run these commands to create a Hugo site with the [Ananke](https://github.com/theNewDynamic/gohugo-theme-ananke) theme. The next section provides an explanation of each command.

```text
hugo new site quickstart
cd quickstart
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo "theme = 'ananke'" >> hugo.toml
hugo server
```

View your site at the URL displayed in your terminal. Press `Ctrl + C` to stop Hugo’s development server.

### Explanation of commands

Create the [directory structure](https://gohugo.io/getting-started/directory-structure/) for your project in the `quickstart` directory.

Change the current directory to the root of your project.

Initialize an empty Git repository in the current directory.

Clone the [Ananke](https://github.com/theNewDynamic/gohugo-theme-ananke) theme into the `themes` directory, adding it to your project as a [Git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

```text
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
```

Append a line to the site configuration file, indicating the current theme.

```text
echo "theme = 'ananke'" >> hugo.toml
```

Start Hugo’s development server to view the site.

Press `Ctrl + C` to stop Hugo’s development server.

## Add content

Add a new page to your site.

```text
hugo new content content/posts/my-first-post.md
```

Hugo created the file in the `content/posts` directory. Open the file with your editor.

```text
+++
title = 'My First Post'
date = 2024-01-14T07:07:07+01:00
draft = true
+++
```

Notice the `draft` value in the [front matter](https://gohugo.io/content-management/front-matter/) is `true`. By default, Hugo does not publish draft content when you build the site. Learn more about [draft, future, and expired content](https://gohugo.io/getting-started/usage/#draft-future-and-expired-content).

Add some [Markdown](https://commonmark.org/help/) to the body of the post, but do not change the `draft` value.

```text
+++
title = 'My First Post'
date = 2024-01-14T07:07:07+01:00
draft = true
+++
## Introduction

This is **bold** text, and this is *emphasized* text.

Visit the [Hugo](https://gohugo.io) website!
```

Save the file, then start Hugo’s development server to view the site. You can run either of the following commands to include draft content.

```text
hugo server --buildDrafts
hugo server -D
```

View your site at the URL displayed in your terminal. Keep the development server running as you continue to add and change content.

When satisfied with your new content, set the front matter `draft` parameter to `false`.

## Configure the site

With your editor, open the [site configuration](https://gohugo.io/getting-started/configuration/) file (`hugo.toml`) in the root of your project.

```text
baseURL = 'https://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
theme = 'ananke'
```

Make the following changes:

1. Set the `baseURL` for your production site. This value must begin with the protocol and end with a slash, as shown above.
2. Set the `languageCode` to your language and region.
3. Set the `title` for your production site.

Start Hugo’s development server to see your changes, remembering to include draft content.

## Publish the site

In this step you will *publish* your site, but you will not *deploy* it.

When you *publish* your site, Hugo creates the entire static site in the `public` directory in the root of your project. This includes the HTML files, and assets such as images, CSS files, and JavaScript files.

When you publish your site, you typically do *not* want to include [draft, future, or expired content](https://gohugo.io/getting-started/usage/#draft-future-and-expired-content). The command is simple.

To learn how to *deploy* your site, see the [hosting and deployment](https://gohugo.io/hosting-and-deployment/) section.

## Ask for help

Hugo’s [forum](https://discourse.gohugo.io/) is an active community of users and developers who answer questions, share knowledge, and provide examples. A quick search of over 20,000 topics will often answer your question. Please be sure to read about [requesting help](https://discourse.gohugo.io/t/requesting-help/9132) before asking your first question.

## Other resources

For other resources to help you learn Hugo, including books and video tutorials, see the [external learning resources](https://gohugo.io/getting-started/external-learning-resources/) page.