---
{"dg-publish":true,"permalink":"/software/hugo-images/","tags":["hugo","html","websites"]}
---

# Hugo Images Static



When working with Hugo, images placed in the `/static` folder are considered global resources and are accessible via their relative path. Here are some key points to remember:

- **Image Paths**: Images in the `/static` folder can be referenced in markdown files using relative paths. For example, if you have an image named `image.png` in `/static/img`, you can reference it as `![Test Image](/img/image.png)`.
    
- **Organizing Images**: It is recommended to organize images within subdirectories of `/static` to keep your project structured. For instance, placing images in `/static/img` and referencing them as `![Test Image](/img/image.png)`.
    
- **Accessing Images in Templates**: If you need to manipulate images using Hugo’s template functions, such as resizing or compressing, you should move the images to the `/assets` folder. You can then use Hugo’s `resources.Get` function to access and modify the images. For example:
    
    ```
    {{ $asset := resources.Get "/duck.png" }}
    {{ $img := $asset.Fit "600x400" }}
    <img src="{{ $img.RelPermalink }}" alt="Duck">
    ```
    
- **Fallback Handling**: To avoid breaking builds due to missing images, you can use Hugo’s `default` function to provide a fallback image. For example:
    
    ```
    {{ $image := .Page.Resources.GetMatch (.Params.cover | default "example.jpg") }}
    <img src="{{ $image.RelPermalink }}" alt="">
    ```
    
- **Linking Images in Org Files**: When using ox-hugo to export Org files to Hugo, you can reference images in the `/static` folder using a simplified path format. For example, if an image is located at `/static/images/foo.png`, you can reference it as `/images/foo.png`.
    
- **Copying External Images**: If you have images located outside the `/static` directory, they can be automatically copied into the `/static` directory by ox-hugo if the path contains `/static/`. If the path does not contain `/static/`, the image will be copied to the `ox-hugo/` directory within `/static`.