---
{"dg-publish":true,"permalink":"/software/open-external-links-in-a-new-tab-in-hugo/","tags":["hugo","websites","design"]}
---

Create a file named`render-link.html` in your theme layouts folder. The order goes like this`layouts/_default/_markup/render-link.html`

layouts
   └── _default  
       └── _markup
           └── render-link.html

Then for the contents of the file`render-link.html` itself is more or less like this:

``` html
<a href="{{ .Destination | safeURL }}"{{ with .Title}} title="{{ . }}"{{ end }}{{ if strings.HasPrefix .Destination "http" }} rel="noopener noreferrer" target="_blank"{{ end }}>{{ .Text }}</a>
```
   
