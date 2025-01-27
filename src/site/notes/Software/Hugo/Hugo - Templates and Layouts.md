---
{"dg-publish":true,"permalink":"/software/hugo/hugo-templates-and-layouts/","tags":["hugo","templates","layouts","howto"]}
---

[[ReadItLater\|ReadItLater]] [[Article\|Article]]

# [Template lookup order](https://gohugo.io/templates/lookup-order/)

## Lookup rules[](https://gohugo.io/templates/lookup-order/#lookup-rules)

Hugo takes the parameters listed below into consideration when choosing a template for a given page. The templates are ordered by specificity. This should feel natural, but look at the table below for concrete examples of the different parameter variations.

Kind

The page `Kind` (the home page is one). See the example tables below per kind. This also determines if it is a **single page** (i.e. a regular content page. We then look for a template in `_default/single.html` for HTML) or a **list page** (section listings, home page, taxonomy lists, taxonomy terms. We then look for a template in `_default/list.html` for HTML).

Layout

Can be set in front matter.

Output Format

See [Custom Output Formats](https://gohugo.io/templates/output-formats/). An output format has both a `name` (e.g. `rss`, `amp`, `html`) and a `suffix` (e.g. `xml`, `html`). We prefer matches with both (e.g. `index.amp.html`), but look for less specific templates.

Note that if the output format’s Media Type has more than one suffix defined, only the first is considered.

Language

We will consider a language tag in the template name. If the site language is `fr`, `index.fr.amp.html` will win over `index.amp.html`, but `index.amp.html` will be chosen before `index.fr.html`.

Type

Is value of `type` if set in front matter, else it is the name of the root section (e.g. “blog”). It will always have a value, so if not set, the value is “page”.

Section

Is relevant for `section`, `taxonomy` and `term` types.

## Target a template[](https://gohugo.io/templates/lookup-order/#target-a-template)

You cannot change the lookup order to target a content page, but you can change a content page to target a template. Specify `type`, `layout`, or both in front matter.

Consider this content structure:

```
content/
├── about.md
└── contact.md
```

Files in the root of the `content` directory have a [content type](https://gohugo.io/getting-started/glossary/#content-type) of `page`. To render these pages with a unique template, create a matching subdirectory:

```
layouts/
└── page/
    └── single.html
```

But the contact page probably has a form and requires a different template. In the front matter specify `layout`:

```
layout: contact
title: Contact
```

```
layout = 'contact'
title = 'Contact'
```

```
{
   "layout": "contact",
   "title": "Contact"
}
```

Then create the template for the contact page:

```
layouts/
└── page/
    └── contact.html  <-- renders contact.md
    └── single.html   <-- renders about.md
```

As a content type, the word `page` is vague. Perhaps `miscellaneous` would be better. Add `type` to the front matter of each page:

```
title: About
type: miscellaneous
```

```
title = 'About'
type = 'miscellaneous'
```

```
{
   "title": "About",
   "type": "miscellaneous"
}
```

```
layout: contact
title: Contact
type: miscellaneous
```

```
layout = 'contact'
title = 'Contact'
type = 'miscellaneous'
```

```
{
   "layout": "contact",
   "title": "Contact",
   "type": "miscellaneous"
}
```

Now place the layouts in the corresponding directory:

```
layouts/
└── miscellaneous/
    └── contact.html  <-- renders contact.md
    └── single.html   <-- renders about.md
```

## Home templates[](https://gohugo.io/templates/lookup-order/#home-templates)

These template paths are sorted by specificity in descending order. The least specific path is at the bottom of each list.

| Example | OutputFormat | Suffix | Template Lookup Order |
| --- | --- | --- | --- |
| Home page | html | html |   1.  layouts/index.html.html 2.  layouts/home.html.html 3.  layouts/list.html.html 4.  layouts/index.html 5.  layouts/home.html 6.  layouts/list.html 7.  layouts/\_default/index.html.html 8.  layouts/\_default/home.html.html 9.  layouts/\_default/list.html.html 10.  layouts/\_default/index.html 11.  layouts/\_default/home.html 12.  layouts/\_default/list.html   |
| Base template for home page | html | html |   1.  layouts/index-baseof.html.html 2.  layouts/home-baseof.html.html 3.  layouts/list-baseof.html.html 4.  layouts/baseof.html.html 5.  layouts/index-baseof.html 6.  layouts/home-baseof.html 7.  layouts/list-baseof.html 8.  layouts/baseof.html 9.  layouts/\_default/index-baseof.html.html 10.  layouts/\_default/home-baseof.html.html 11.  layouts/\_default/list-baseof.html.html 12.  layouts/\_default/baseof.html.html 13.  layouts/\_default/index-baseof.html 14.  layouts/\_default/home-baseof.html 15.  layouts/\_default/list-baseof.html 16.  layouts/\_default/baseof.html   |
| Home page with type set to "demotype" | html | html |   1.  layouts/demotype/index.html.html 2.  layouts/demotype/home.html.html 3.  layouts/demotype/list.html.html 4.  layouts/demotype/index.html 5.  layouts/demotype/home.html 6.  layouts/demotype/list.html 7.  layouts/index.html.html 8.  layouts/home.html.html 9.  layouts/list.html.html 10.  layouts/index.html 11.  layouts/home.html 12.  layouts/list.html 13.  layouts/\_default/index.html.html 14.  layouts/\_default/home.html.html 15.  layouts/\_default/list.html.html 16.  layouts/\_default/index.html 17.  layouts/\_default/home.html 18.  layouts/\_default/list.html   |
| Base template for home page with type set to "demotype" | html | html |   1.  layouts/demotype/index-baseof.html.html 2.  layouts/demotype/home-baseof.html.html 3.  layouts/demotype/list-baseof.html.html 4.  layouts/demotype/baseof.html.html 5.  layouts/demotype/index-baseof.html 6.  layouts/demotype/home-baseof.html 7.  layouts/demotype/list-baseof.html 8.  layouts/demotype/baseof.html 9.  layouts/index-baseof.html.html 10.  layouts/home-baseof.html.html 11.  layouts/list-baseof.html.html 12.  layouts/baseof.html.html 13.  layouts/index-baseof.html 14.  layouts/home-baseof.html 15.  layouts/list-baseof.html 16.  layouts/baseof.html 17.  layouts/\_default/index-baseof.html.html 18.  layouts/\_default/home-baseof.html.html 19.  layouts/\_default/list-baseof.html.html 20.  layouts/\_default/baseof.html.html 21.  layouts/\_default/index-baseof.html 22.  layouts/\_default/home-baseof.html 23.  layouts/\_default/list-baseof.html 24.  layouts/\_default/baseof.html   |
| Home page with layout set to "demolayout" | html | html |   1.  layouts/demolayout.html.html 2.  layouts/index.html.html 3.  layouts/home.html.html 4.  layouts/list.html.html 5.  layouts/demolayout.html 6.  layouts/index.html 7.  layouts/home.html 8.  layouts/list.html 9.  layouts/\_default/demolayout.html.html 10.  layouts/\_default/index.html.html 11.  layouts/\_default/home.html.html 12.  layouts/\_default/list.html.html 13.  layouts/\_default/demolayout.html 14.  layouts/\_default/index.html 15.  layouts/\_default/home.html 16.  layouts/\_default/list.html   |
| AMP home, French language | amp | html |   1.  layouts/index.fr.amp.html 2.  layouts/home.fr.amp.html 3.  layouts/list.fr.amp.html 4.  layouts/index.amp.html 5.  layouts/home.amp.html 6.  layouts/list.amp.html 7.  layouts/index.fr.html 8.  layouts/home.fr.html 9.  layouts/list.fr.html 10.  layouts/index.html 11.  layouts/home.html 12.  layouts/list.html 13.  layouts/\_default/index.fr.amp.html 14.  layouts/\_default/home.fr.amp.html 15.  layouts/\_default/list.fr.amp.html 16.  layouts/\_default/index.amp.html 17.  layouts/\_default/home.amp.html 18.  layouts/\_default/list.amp.html 19.  layouts/\_default/index.fr.html 20.  layouts/\_default/home.fr.html 21.  layouts/\_default/list.fr.html 22.  layouts/\_default/index.html 23.  layouts/\_default/home.html 24.  layouts/\_default/list.html   |
| JSON home | json | json |   1.  layouts/index.json.json 2.  layouts/home.json.json 3.  layouts/list.json.json 4.  layouts/index.json 5.  layouts/home.json 6.  layouts/list.json 7.  layouts/\_default/index.json.json 8.  layouts/\_default/home.json.json 9.  layouts/\_default/list.json.json 10.  layouts/\_default/index.json 11.  layouts/\_default/home.json 12.  layouts/\_default/list.json   |
| RSS home | rss | xml |   1.  layouts/index.rss.xml 2.  layouts/home.rss.xml 3.  layouts/rss.xml 4.  layouts/list.rss.xml 5.  layouts/index.xml 6.  layouts/home.xml 7.  layouts/list.xml 8.  layouts/\_default/index.rss.xml 9.  layouts/\_default/home.rss.xml 10.  layouts/\_default/rss.xml 11.  layouts/\_default/list.rss.xml 12.  layouts/\_default/index.xml 13.  layouts/\_default/home.xml 14.  layouts/\_default/list.xml 15.  layouts/\_internal/\_default/rss.xml   |

## Single templates[](https://gohugo.io/templates/lookup-order/#single-templates)

These template paths are sorted by specificity in descending order. The least specific path is at the bottom of each list.

| Example | OutputFormat | Suffix | Template Lookup Order |
| --- | --- | --- | --- |
| Single page in "posts" section | html | html |   1.  layouts/posts/single.html.html 2.  layouts/posts/single.html 3.  layouts/\_default/single.html.html 4.  layouts/\_default/single.html   |
| Base template for single page in "posts" section | html | html |   1.  layouts/posts/single-baseof.html.html 2.  layouts/posts/baseof.html.html 3.  layouts/posts/single-baseof.html 4.  layouts/posts/baseof.html 5.  layouts/\_default/single-baseof.html.html 6.  layouts/\_default/baseof.html.html 7.  layouts/\_default/single-baseof.html 8.  layouts/\_default/baseof.html   |
| Single page in "posts" section with layout set to "demolayout" | html | html |   1.  layouts/posts/demolayout.html.html 2.  layouts/posts/single.html.html 3.  layouts/posts/demolayout.html 4.  layouts/posts/single.html 5.  layouts/\_default/demolayout.html.html 6.  layouts/\_default/single.html.html 7.  layouts/\_default/demolayout.html 8.  layouts/\_default/single.html   |
| Base template for single page in "posts" section with layout set to "demolayout" | html | html |   1.  layouts/posts/demolayout-baseof.html.html 2.  layouts/posts/single-baseof.html.html 3.  layouts/posts/baseof.html.html 4.  layouts/posts/demolayout-baseof.html 5.  layouts/posts/single-baseof.html 6.  layouts/posts/baseof.html 7.  layouts/\_default/demolayout-baseof.html.html 8.  layouts/\_default/single-baseof.html.html 9.  layouts/\_default/baseof.html.html 10.  layouts/\_default/demolayout-baseof.html 11.  layouts/\_default/single-baseof.html 12.  layouts/\_default/baseof.html   |
| AMP single page in "posts" section | amp | html |   1.  layouts/posts/single.amp.html 2.  layouts/posts/single.html 3.  layouts/\_default/single.amp.html 4.  layouts/\_default/single.html   |
| AMP single page in "posts" section, French language | amp | html |   1.  layouts/posts/single.fr.amp.html 2.  layouts/posts/single.amp.html 3.  layouts/posts/single.fr.html 4.  layouts/posts/single.html 5.  layouts/\_default/single.fr.amp.html 6.  layouts/\_default/single.amp.html 7.  layouts/\_default/single.fr.html 8.  layouts/\_default/single.html   |

## Section templates[](https://gohugo.io/templates/lookup-order/#section-templates)

These template paths are sorted by specificity in descending order. The least specific path is at the bottom of each list.

| Example | OutputFormat | Suffix | Template Lookup Order |
| --- | --- | --- | --- |
| Section list for "posts" | html | html |   1.  layouts/posts/posts.html.html 2.  layouts/posts/section.html.html 3.  layouts/posts/list.html.html 4.  layouts/posts/posts.html 5.  layouts/posts/section.html 6.  layouts/posts/list.html 7.  layouts/section/posts.html.html 8.  layouts/section/section.html.html 9.  layouts/section/list.html.html 10.  layouts/section/posts.html 11.  layouts/section/section.html 12.  layouts/section/list.html 13.  layouts/\_default/posts.html.html 14.  layouts/\_default/section.html.html 15.  layouts/\_default/list.html.html 16.  layouts/\_default/posts.html 17.  layouts/\_default/section.html 18.  layouts/\_default/list.html   |
| Section list for "posts" with type set to "blog" | html | html |   1.  layouts/blog/posts.html.html 2.  layouts/blog/section.html.html 3.  layouts/blog/list.html.html 4.  layouts/blog/posts.html 5.  layouts/blog/section.html 6.  layouts/blog/list.html 7.  layouts/posts/posts.html.html 8.  layouts/posts/section.html.html 9.  layouts/posts/list.html.html 10.  layouts/posts/posts.html 11.  layouts/posts/section.html 12.  layouts/posts/list.html 13.  layouts/section/posts.html.html 14.  layouts/section/section.html.html 15.  layouts/section/list.html.html 16.  layouts/section/posts.html 17.  layouts/section/section.html 18.  layouts/section/list.html 19.  layouts/\_default/posts.html.html 20.  layouts/\_default/section.html.html 21.  layouts/\_default/list.html.html 22.  layouts/\_default/posts.html 23.  layouts/\_default/section.html 24.  layouts/\_default/list.html   |
| Section list for "posts" with layout set to "demolayout" | html | html |   1.  layouts/posts/demolayout.html.html 2.  layouts/posts/posts.html.html 3.  layouts/posts/section.html.html 4.  layouts/posts/list.html.html 5.  layouts/posts/demolayout.html 6.  layouts/posts/posts.html 7.  layouts/posts/section.html 8.  layouts/posts/list.html 9.  layouts/section/demolayout.html.html 10.  layouts/section/posts.html.html 11.  layouts/section/section.html.html 12.  layouts/section/list.html.html 13.  layouts/section/demolayout.html 14.  layouts/section/posts.html 15.  layouts/section/section.html 16.  layouts/section/list.html 17.  layouts/\_default/demolayout.html.html 18.  layouts/\_default/posts.html.html 19.  layouts/\_default/section.html.html 20.  layouts/\_default/list.html.html 21.  layouts/\_default/demolayout.html 22.  layouts/\_default/posts.html 23.  layouts/\_default/section.html 24.  layouts/\_default/list.html   |
| Section list for "posts" | rss | xml |   1.  layouts/posts/section.rss.xml 2.  layouts/posts/rss.xml 3.  layouts/posts/list.rss.xml 4.  layouts/posts/section.xml 5.  layouts/posts/list.xml 6.  layouts/section/section.rss.xml 7.  layouts/section/rss.xml 8.  layouts/section/list.rss.xml 9.  layouts/section/section.xml 10.  layouts/section/list.xml 11.  layouts/\_default/section.rss.xml 12.  layouts/\_default/rss.xml 13.  layouts/\_default/list.rss.xml 14.  layouts/\_default/section.xml 15.  layouts/\_default/list.xml 16.  layouts/\_internal/\_default/rss.xml   |

## Taxonomy templates[](https://gohugo.io/templates/lookup-order/#taxonomy-templates)

These template paths are sorted by specificity in descending order. The least specific path is at the bottom of each list.

The examples below assume the following site configuration:

```
taxonomies:
  category: categories
```

```
[taxonomies]
  category = 'categories'
```

```
{
   "taxonomies": {
      "category": "categories"
   }
}
```

| Example | OutputFormat | Suffix | Template Lookup Order |
| --- | --- | --- | --- |
| Taxonomy list for "categories" | html | html |   1.  layouts/categories/category.terms.html.html 2.  layouts/categories/terms.html.html 3.  layouts/categories/taxonomy.html.html 4.  layouts/categories/list.html.html 5.  layouts/categories/category.terms.html 6.  layouts/categories/terms.html 7.  layouts/categories/taxonomy.html 8.  layouts/categories/list.html 9.  layouts/category/category.terms.html.html 10.  layouts/category/terms.html.html 11.  layouts/category/taxonomy.html.html 12.  layouts/category/list.html.html 13.  layouts/category/category.terms.html 14.  layouts/category/terms.html 15.  layouts/category/taxonomy.html 16.  layouts/category/list.html 17.  layouts/taxonomy/category.terms.html.html 18.  layouts/taxonomy/terms.html.html 19.  layouts/taxonomy/taxonomy.html.html 20.  layouts/taxonomy/list.html.html 21.  layouts/taxonomy/category.terms.html 22.  layouts/taxonomy/terms.html 23.  layouts/taxonomy/taxonomy.html 24.  layouts/taxonomy/list.html 25.  layouts/\_default/category.terms.html.html 26.  layouts/\_default/terms.html.html 27.  layouts/\_default/taxonomy.html.html 28.  layouts/\_default/list.html.html 29.  layouts/\_default/category.terms.html 30.  layouts/\_default/terms.html 31.  layouts/\_default/taxonomy.html 32.  layouts/\_default/list.html   |
| Taxonomy list for "categories" | rss | xml |   1.  layouts/categories/category.terms.rss.xml 2.  layouts/categories/terms.rss.xml 3.  layouts/categories/taxonomy.rss.xml 4.  layouts/categories/rss.xml 5.  layouts/categories/list.rss.xml 6.  layouts/categories/category.terms.xml 7.  layouts/categories/terms.xml 8.  layouts/categories/taxonomy.xml 9.  layouts/categories/list.xml 10.  layouts/category/category.terms.rss.xml 11.  layouts/category/terms.rss.xml 12.  layouts/category/taxonomy.rss.xml 13.  layouts/category/rss.xml 14.  layouts/category/list.rss.xml 15.  layouts/category/category.terms.xml 16.  layouts/category/terms.xml 17.  layouts/category/taxonomy.xml 18.  layouts/category/list.xml 19.  layouts/taxonomy/category.terms.rss.xml 20.  layouts/taxonomy/terms.rss.xml 21.  layouts/taxonomy/taxonomy.rss.xml 22.  layouts/taxonomy/rss.xml 23.  layouts/taxonomy/list.rss.xml 24.  layouts/taxonomy/category.terms.xml 25.  layouts/taxonomy/terms.xml 26.  layouts/taxonomy/taxonomy.xml 27.  layouts/taxonomy/list.xml 28.  layouts/\_default/category.terms.rss.xml 29.  layouts/\_default/terms.rss.xml 30.  layouts/\_default/taxonomy.rss.xml 31.  layouts/\_default/rss.xml 32.  layouts/\_default/list.rss.xml 33.  layouts/\_default/category.terms.xml 34.  layouts/\_default/terms.xml 35.  layouts/\_default/taxonomy.xml 36.  layouts/\_default/list.xml 37.  layouts/\_internal/\_default/rss.xml   |

## Term templates[](https://gohugo.io/templates/lookup-order/#term-templates)

These template paths are sorted by specificity in descending order. The least specific path is at the bottom of each list.

The examples below assume the following site configuration:

```
taxonomies:
  category: categories
```

```
[taxonomies]
  category = 'categories'
```

```
{
   "taxonomies": {
      "category": "categories"
   }
}
```

| Example | OutputFormat | Suffix | Template Lookup Order |
| --- | --- | --- | --- |
| Term list for "categories" | html | html |   1.  layouts/categories/term.html.html 2.  layouts/categories/category.html.html 3.  layouts/categories/taxonomy.html.html 4.  layouts/categories/list.html.html 5.  layouts/categories/term.html 6.  layouts/categories/category.html 7.  layouts/categories/taxonomy.html 8.  layouts/categories/list.html 9.  layouts/term/term.html.html 10.  layouts/term/category.html.html 11.  layouts/term/taxonomy.html.html 12.  layouts/term/list.html.html 13.  layouts/term/term.html 14.  layouts/term/category.html 15.  layouts/term/taxonomy.html 16.  layouts/term/list.html 17.  layouts/taxonomy/term.html.html 18.  layouts/taxonomy/category.html.html 19.  layouts/taxonomy/taxonomy.html.html 20.  layouts/taxonomy/list.html.html 21.  layouts/taxonomy/term.html 22.  layouts/taxonomy/category.html 23.  layouts/taxonomy/taxonomy.html 24.  layouts/taxonomy/list.html 25.  layouts/category/term.html.html 26.  layouts/category/category.html.html 27.  layouts/category/taxonomy.html.html 28.  layouts/category/list.html.html 29.  layouts/category/term.html 30.  layouts/category/category.html 31.  layouts/category/taxonomy.html 32.  layouts/category/list.html 33.  layouts/\_default/term.html.html 34.  layouts/\_default/category.html.html 35.  layouts/\_default/taxonomy.html.html 36.  layouts/\_default/list.html.html 37.  layouts/\_default/term.html 38.  layouts/\_default/category.html 39.  layouts/\_default/taxonomy.html 40.  layouts/\_default/list.html   |
| Term list for "categories" | rss | xml |   1.  layouts/categories/term.rss.xml 2.  layouts/categories/category.rss.xml 3.  layouts/categories/taxonomy.rss.xml 4.  layouts/categories/rss.xml 5.  layouts/categories/list.rss.xml 6.  layouts/categories/term.xml 7.  layouts/categories/category.xml 8.  layouts/categories/taxonomy.xml 9.  layouts/categories/list.xml 10.  layouts/term/term.rss.xml 11.  layouts/term/category.rss.xml 12.  layouts/term/taxonomy.rss.xml 13.  layouts/term/rss.xml 14.  layouts/term/list.rss.xml 15.  layouts/term/term.xml 16.  layouts/term/category.xml 17.  layouts/term/taxonomy.xml 18.  layouts/term/list.xml 19.  layouts/taxonomy/term.rss.xml 20.  layouts/taxonomy/category.rss.xml 21.  layouts/taxonomy/taxonomy.rss.xml 22.  layouts/taxonomy/rss.xml 23.  layouts/taxonomy/list.rss.xml 24.  layouts/taxonomy/term.xml 25.  layouts/taxonomy/category.xml 26.  layouts/taxonomy/taxonomy.xml 27.  layouts/taxonomy/list.xml 28.  layouts/category/term.rss.xml 29.  layouts/category/category.rss.xml 30.  layouts/category/taxonomy.rss.xml 31.  layouts/category/rss.xml 32.  layouts/category/list.rss.xml 33.  layouts/category/term.xml 34.  layouts/category/category.xml 35.  layouts/category/taxonomy.xml 36.  layouts/category/list.xml 37.  layouts/\_default/term.rss.xml 38.  layouts/\_default/category.rss.xml 39.  layouts/\_default/taxonomy.rss.xml 40.  layouts/\_default/rss.xml 41.  layouts/\_default/list.rss.xml 42.  layouts/\_default/term.xml 43.  layouts/\_default/category.xml 44.  layouts/\_default/taxonomy.xml 45.  layouts/\_default/list.xml 46.  layouts/\_internal/\_default/rss.xml   |

These template paths are sorted by specificity in descending order. The least specific path is at the bottom of each list.

The examples below assume the following site configuration:

```
taxonomies:
  category: categories
```

```
[taxonomies]
  category = 'categories'
```

```
{
   "taxonomies": {
      "category": "categories"
   }
}
```

| Example | OutputFormat | Suffix | Template Lookup Order |
| --- | --- | --- | --- |
| RSS home | rss | xml |   1.  layouts/index.rss.xml 2.  layouts/home.rss.xml 3.  layouts/rss.xml 4.  layouts/list.rss.xml 5.  layouts/index.xml 6.  layouts/home.xml 7.  layouts/list.xml 8.  layouts/\_default/index.rss.xml 9.  layouts/\_default/home.rss.xml 10.  layouts/\_default/rss.xml 11.  layouts/\_default/list.rss.xml 12.  layouts/\_default/index.xml 13.  layouts/\_default/home.xml 14.  layouts/\_default/list.xml 15.  layouts/\_internal/\_default/rss.xml   |
| Section list for "posts" | rss | xml |   1.  layouts/posts/section.rss.xml 2.  layouts/posts/rss.xml 3.  layouts/posts/list.rss.xml 4.  layouts/posts/section.xml 5.  layouts/posts/list.xml 6.  layouts/section/section.rss.xml 7.  layouts/section/rss.xml 8.  layouts/section/list.rss.xml 9.  layouts/section/section.xml 10.  layouts/section/list.xml 11.  layouts/\_default/section.rss.xml 12.  layouts/\_default/rss.xml 13.  layouts/\_default/list.rss.xml 14.  layouts/\_default/section.xml 15.  layouts/\_default/list.xml 16.  layouts/\_internal/\_default/rss.xml   |
| Taxonomy list for "categories" | rss | xml |   1.  layouts/categories/category.terms.rss.xml 2.  layouts/categories/terms.rss.xml 3.  layouts/categories/taxonomy.rss.xml 4.  layouts/categories/rss.xml 5.  layouts/categories/list.rss.xml 6.  layouts/categories/category.terms.xml 7.  layouts/categories/terms.xml 8.  layouts/categories/taxonomy.xml 9.  layouts/categories/list.xml 10.  layouts/category/category.terms.rss.xml 11.  layouts/category/terms.rss.xml 12.  layouts/category/taxonomy.rss.xml 13.  layouts/category/rss.xml 14.  layouts/category/list.rss.xml 15.  layouts/category/category.terms.xml 16.  layouts/category/terms.xml 17.  layouts/category/taxonomy.xml 18.  layouts/category/list.xml 19.  layouts/taxonomy/category.terms.rss.xml 20.  layouts/taxonomy/terms.rss.xml 21.  layouts/taxonomy/taxonomy.rss.xml 22.  layouts/taxonomy/rss.xml 23.  layouts/taxonomy/list.rss.xml 24.  layouts/taxonomy/category.terms.xml 25.  layouts/taxonomy/terms.xml 26.  layouts/taxonomy/taxonomy.xml 27.  layouts/taxonomy/list.xml 28.  layouts/\_default/category.terms.rss.xml 29.  layouts/\_default/terms.rss.xml 30.  layouts/\_default/taxonomy.rss.xml 31.  layouts/\_default/rss.xml 32.  layouts/\_default/list.rss.xml 33.  layouts/\_default/category.terms.xml 34.  layouts/\_default/terms.xml 35.  layouts/\_default/taxonomy.xml 36.  layouts/\_default/list.xml 37.  layouts/\_internal/\_default/rss.xml   |
| Term list for "categories" | rss | xml |   1.  layouts/categories/term.rss.xml 2.  layouts/categories/category.rss.xml 3.  layouts/categories/taxonomy.rss.xml 4.  layouts/categories/rss.xml 5.  layouts/categories/list.rss.xml 6.  layouts/categories/term.xml 7.  layouts/categories/category.xml 8.  layouts/categories/taxonomy.xml 9.  layouts/categories/list.xml 10.  layouts/term/term.rss.xml 11.  layouts/term/category.rss.xml 12.  layouts/term/taxonomy.rss.xml 13.  layouts/term/rss.xml 14.  layouts/term/list.rss.xml 15.  layouts/term/term.xml 16.  layouts/term/category.xml 17.  layouts/term/taxonomy.xml 18.  layouts/term/list.xml 19.  layouts/taxonomy/term.rss.xml 20.  layouts/taxonomy/category.rss.xml 21.  layouts/taxonomy/taxonomy.rss.xml 22.  layouts/taxonomy/rss.xml 23.  layouts/taxonomy/list.rss.xml 24.  layouts/taxonomy/term.xml 25.  layouts/taxonomy/category.xml 26.  layouts/taxonomy/taxonomy.xml 27.  layouts/taxonomy/list.xml 28.  layouts/category/term.rss.xml 29.  layouts/category/category.rss.xml 30.  layouts/category/taxonomy.rss.xml 31.  layouts/category/rss.xml 32.  layouts/category/list.rss.xml 33.  layouts/category/term.xml 34.  layouts/category/category.xml 35.  layouts/category/taxonomy.xml 36.  layouts/category/list.xml 37.  layouts/\_default/term.rss.xml 38.  layouts/\_default/category.rss.xml 39.  layouts/\_default/taxonomy.rss.xml 40.  layouts/\_default/rss.xml 41.  layouts/\_default/list.rss.xml 42.  layouts/\_default/term.xml 43.  layouts/\_default/category.xml 44.  layouts/\_default/taxonomy.xml 45.  layouts/\_default/list.xml 46.  layouts/\_internal/\_default/rss.xml   |