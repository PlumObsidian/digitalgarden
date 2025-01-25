---
{"dg-publish":true,"permalink":"/software/hugo/hugo-new-content-and-archetypes/","tags":["hugo","software","tools"]}
---

In the "archetypes" folder you can set up some templates for new post or content types.

You can start by editing the default and saving as a youtube.md archetype.

Something like this;

```
---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date }}
type: "post"
tags: 
  - "Music"
  - "Youtube"
image: "youtube/someimage.jpg"
description: ""
categories:
  - "Music"
---

{{< youtube Xxxxxxxx >}}
```

From your base Hugo directory you can now use the "-k" flag for a new post to use this archetype template. I think if you remove the default then hugo should determine the post type [intelligently]([hugo new | Hugo](https://gohugo.io/commands/hugo_new/)) from the directory structure..

```

hugo new -k youtube content/blog/youtubel/mynewyoutubepost.md
```

