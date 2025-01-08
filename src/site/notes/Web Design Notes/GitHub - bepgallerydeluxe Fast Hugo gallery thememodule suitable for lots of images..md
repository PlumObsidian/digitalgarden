---
{"dg-publish":true,"permalink":"/web-design-notes/git-hub-bepgallerydeluxe-fast-hugo-gallery-thememodule-suitable-for-lots-of-images/"}
---

[[ReadItLater\|ReadItLater]] [[Article\|Article]]

[[Linux Cheat Sheets/Hugo images\|Hugo images]]  [Hugo](https://gohugo.io/)
# [GitHub - bep/gallerydeluxe: Fast Hugo gallery theme/module suitable for lots of images.](https://github.com/bep/gallerydeluxe?tab=readme-ov-file)

> **Note 1:** See this [Gallery Deluxe Starter](https://github.com/bep/gallerydeluxe_starter) for a fast route to get this up and running.

> **Note 2:** If you need *multiple* galleries, see [Galleries Deluxe](https://github.com/bep/galleriesdeluxe).

---

-   [Configuration](https://github.com/bep/gallerydeluxe?tab=readme-ov-file#configuration)
-   [Credits](https://github.com/bep/gallerydeluxe?tab=readme-ov-file#credits)

A Hugo Module to show a photo gallery. It's very fast/effective, especially if you have lots of images on display.

This theme is what you see on [staticbattery.com](https://staticbattery.com/) which, at the time of writing this, [scores 100](https://pagespeed.web.dev/report?url=https%3A%2F%2Fstaticbattery.com%2F&form_factor=mobile) at Google PageSpeed for both mobile and desktop.

[![](https://raw.githubusercontent.com/bep/gallerydeluxe/main/images/tn.jpg)](https://staticbattery.com/)

## Configuration

[](https://github.com/bep/gallerydeluxe?tab=readme-ov-file#configuration)

The recommended way to add this to your site is to include it as a Hugo Module. See [Gallery Deluxe Starter](https://github.com/bep/gallerydeluxe_starter) for a starter template. Another example is [staticbattery.com](https://github.com/bep/staticbattery.com).

### Params

[](https://github.com/bep/gallerydeluxe?tab=readme-ov-file#params)

\[params\]
    \[params.gallerydeluxe\]
        # Shuffle the images in the gallery to give the impression of a new gallery each time.
        shuffle = false

        # Reverse the order of the images in the gallery.
        reverse = false

         # Enable Exif data in the gallery.
         # See https://gohugo.io/content-management/image-processing/#exif-data for how to filter tags.
        enable\_exif = false

          # Optional watermark file for the large images.
        \[params.gallerydeluxe.watermark\]
            image = "images/gopher-hero8.png" # relative to /assets
            posx  = "left"                    # one of "left", "center", "right"
            posy  = "bottom"                  # one of "top", "center", "bottom"

If you want full control over how your images gets created, create and adjust a copy of [layouts/partials/gallerydeluxe/create-thumbs.html](https://github.com/bep/gallerydeluxe/blob/main/layouts/partials/gallerydeluxe/create-thumbs.html) into your own project.

## Credits

[](https://github.com/bep/gallerydeluxe?tab=readme-ov-file#credits)

Credit to Dan Schlosser for the [Pig](https://github.com/schlosser/pig.js) JS library.