---
{"dg-publish":true,"permalink":"/software/hugo/hugo-index-md-function/","tags":["hugo","design","websites","_index"]}
---


#_index.md

Hugo _index.md

In Hugo, the `_index.md` file plays a crucial role in organizing and displaying content for sections, taxonomies, and terms. Here are some key points about using `_index.md`:

- **Location and Purpose**: An `_index.md` file is used to add content and front matter to home, section, taxonomy, and term pages. It should be placed in the relevant directory within the `content` folder. For example, to add content and front matter to the home page, you would place `_index.md` in the top-level `content` directory.
    
- **Rendering**: The content and front matter in `_index.md` are rendered by specific templates. For instance, the home page might use `layouts/index.html`, while section pages use templates like `layouts/section/post.html`.
    
- **Structure and Nesting**: Sections can be nested as deeply as needed. However, to ensure full navigability, the lowest-level section must include a content file, typically named `_index.md`.
    
- **Content Type and Layouts**: The top-level folders in the `content` directory are special in Hugo and determine the content type and associated layouts. For example, `content/posts/_index.md` and `content/categories/_index.md` are used to manage posts and categories, respectively.
    
- **Content Management**: If you need to use a different file name for the homepage content, such as `intro.md`, you can use Hugo’s `GetPage` function in your template to render the content from that file. For example:
    
    ```
    {{- (.Site.GetPage "intro").Content -}}
    ```
    
- **Page Bundles**: `_index.md` files are part of branch bundles, which allow for nested content and navigable URLs for subfolders. In contrast, leaf bundles use `index.md` and do not create navigable URLs for sibling pages.