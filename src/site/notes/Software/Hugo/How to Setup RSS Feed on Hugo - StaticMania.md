---
{"dg-publish":true,"permalink":"/software/hugo/how-to-setup-rss-feed-on-hugo-static-mania/","tags":["hugo","rss","tutorials"]}
---

[[ReadItLater\|ReadItLater]] [[Article\|Article]]

# [How to Setup RSS Feed on Hugo - StaticMania](https://staticmania.com/blog/how-to-setup-rss-feed-on-hugo)

RSS stands for "Really Simple Syndication". It is a web feed technology that allows users to receive updates from websites or online publications. Whether you're running a blog, an e-commerce site, or a portfolio, an RSS feed will enhance the accessibility and reach of your content. In this guide, we'll cover everything about configuring the RSS feed.

## Synopsis

When you generate a [website using Hugo](https://staticmania.com/blog/why-you-should-use-hugo), the [static site generator](https://staticmania.com/blog/static-site-generators), it generates an RSS feed by default. The RSS feed is based on the RSS 2.0 specification and follows a standardised XML format. The default RSS feed template provided by Hugo is functional and adheres to this specification, making it suitable for most use cases.

The RSS XML index.xml is auto-generated for -

-   Homepage for the whole website e.g. https://example.com/index.xml
-   Section’s  for the website e.g. https://example.com/<SECTION>/index.xml
-   Taxonomy Term for each taxonomy term e.g. https://example.com/categories/index.xml
-   Taxonomy for each taxonomy, e.g. [https://example.com/categories/](https://example.com/categories/)<CATEGORY>/index.xml

## Configure RSS Feed

You can configure Hugo to include copyright notices, set author information, and customize other metadata in your site's RSS feed by updating the config.toml file. Here's how you can do it:

1\. You can specify the author information for your site in the config.toml file under the \[author\] section. Here's an example of how to configure the author's name and email:

```
[Author]
    name = "Justin James"
    email  = "me@example.com"
```

2\. To add a Copyright notice to your site, add a Copyright parameter in the config.toml file. For example:

Copyright = "© 2023 MyWebsite. All rights reserved."

## Custom RSS Template

Hugo has a built-in RSS template. However, you can modify the template as needed to fit your site's requirements. The following steps will show you how to customize your RSS feed:

**Create the RSS Template:**

Hugo's default RSS template is typically located in the theme you are using. It should be in a path like themes/your-theme-name/layouts/\_default/rss.xml or layouts/\_default/rss.xml.

If there is not any rss.xml file in the themes/your-theme-name/layouts/\_default/ or  layouts/\_default/ folder, just create one.

**Copy the Default RSS Template:**

Copy the [hugo’s default RSS template](https://github.com/gohugoio/hugo/blob/master/tpl/tplimpl/embedded/templates/_default/rss.xml) and paste it into the themes/your-theme-name/layouts/\_default/rss.xml or layouts/\_default/rss.xml file.

**Customize the RSS Template:**

Open the copied rss.xml file in a text editor and make the desired customizations. You can adjust the structure, content, and styling of your RSS feed to match your website's branding and requirements.

**Regenerate Your Site:**

After making changes to your custom RSS template, regenerate your Hugo site using the Hugo command to apply the custom template:

```
hugo
```

Your customized RSS feed will now be generated according to the modifications you made to the rss.xml file in the layouts/\_default directory of your Hugo project. This approach allows you to have full control over the appearance and content of your RSS feed.

## Disable RSS Feed generation

To disable the generation of a sitemap in Hugo, you can simply add the following line of code in the config.toml file.

```
disableKinds = [rss]
```

In conclusion, adding an RSS feed to your Hugo website is a valuable way to keep your audience informed and engaged. Whether you're running a blog, news site, or any other type of web project, an RSS feed ensures that your visitors receive timely updates and can easily follow your content. By implementing this feature, you enhance the accessibility and reach of your website, providing a seamless connection between your site and your audience's favourite feed readers. Stay connected, stay informed, and keep your visitors coming back for more.

Not sure where to begin? You need not look any further; [Staticmania](https://staticmania.com/) is the answer! [Our devoted team](https://staticmania.com/service/jamstack-website) of HUGO professionals is ready to lead you through each stage of your journey. Don't wait; [get in touch](https://staticmania.com/contact) with us right now to start your experience.

How To Enabling Comments on Hugo Website with Commento

![thumbnail](/img/user/ReadItLater%20Inbox/assets/thumbnail.jpg)

#### Enabling Comments on Hugo Website with Commento

Enable comments and discussions on your Hugo website effortlessly with Commento, a user-friendly and ad-free commenting system that enhances user engagement.

[Read article](https://staticmania.com/blog/enabling-comments-on-hugo-website-with-commento)