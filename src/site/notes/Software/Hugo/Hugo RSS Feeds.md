---
{"dg-publish":true,"permalink":"/software/hugo/hugo-rss-feeds/","tags":["hugo","rss","howto","websites"]}
---

# Hugo RSS Feed Setup

Hugo, a static site generator, supports RSS feeds out of the box. Here are some key points about setting up and customizing RSS feeds in Hugo:

- **Default RSS Feed**: Hugo comes with a default RSS template that adheres to the RSS 2.0 specification. This template is typically located in the theme directory at `layouts/_default/rss.xml`.
    
- **Enabling RSS Feed**: To enable RSS feeds for specific sections or pages, you can configure the `outputs` in your `config.toml` file. For example, to enable RSS feeds only for the blog section, you can set:
    
    ```
    [outputs]
    home = ["html"]
    section = ["html", "rss"]
    taxonomy = ["html"]
    term = ["html"]
    ```
    
    Then, in your blog section's front matter, specify:
    
    ```
    title = "Blog"
    outputs = ["html", "rss"]
    ```
    
- **Customizing RSS Feed**: You can customize the default RSS template by copying it to your theme's `layouts/_default/rss.xml` and modifying it according to your needs. This allows you to adjust the structure, content, and styling of your RSS feed.
    
- **Including RSS Link in Header**: To include an RSS link in your site's header for easy discovery, you can add the following code snippet to your `header.html` template:
    
    ```
    {{ if .RSSLink }}
      <link href="{{ .RSSLink }}" rel="alternate" type="application/rss+xml" title="{{ .Site.Title }}" />
    {{ end }}
    ```
    
- **Full Content in RSS Feed**: By default, the RSS feed may only include summaries of posts. To include full content, you may need to modify the RSS template to ensure the full content is included in the `<content:encoded>` tag.
    
- **Testing RSS Feed**: You can test the generated RSS XML file locally by running your Hugo server and opening the `index.xml` file in your RSS reader or using an online RSS validator.