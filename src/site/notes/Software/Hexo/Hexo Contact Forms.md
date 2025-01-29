---
{"dg-publish":true,"permalink":"/software/hexo/hexo-contact-forms/","tags":["hexo","websites","software"]}
---

# Hexo Contact Forms

Hexo Contact Form

To set up a contact form on a Hexo static site, you can follow these steps:

1. **Create a Contact Page**:
    
    - Use the command line to create a new page for your contact form:
        
        ```
        hexo new page contact
        ```
        
    - This will create a directory named `contact` with an `index.md` file inside it. You can customize the content of this file to include your contact form HTML.
2. **Integrate FormSpree**:
    
    - For a simple and effective solution, you can use FormSpree to handle form submissions without needing a server. FormSpree provides a basic HTML form structure that you can copy into your `index.md` file.
    - Add additional HTML5 elements to enhance the form’s functionality, such as `fieldset`, `placeholder`, and `required` attributes.
3. **Styling and Customization**:
    
    - You can add CSS classes and JavaScript to style your form and add interactive effects. For example, you can use classes and IDs to apply styles and add a loading spinner on the submit button.
4. **Testing**:
    
    - After setting up your form, you can test it by running a local server:
        
        ```
        hexo server
        ```
        
    - Navigate to `http://localhost:4000/contact/` to check your form.

Alternatively, you can use a third-party service like Getform to create a more advanced contact form with additional fields and features. Here’s how you can integrate Getform:

1. **Create a Form on Getform**:
    
    - Log in to Getform and create a new form named, for example, “Contact Form for my Hexo Site”.
    - Copy the unique endpoint URL provided by Getform.
2. **Embed the Form in Hexo**:
    
    - Use the boilerplate code provided by Getform to create your HTML form.
    - Integrate this form into your Hexo site by adding the HTML code to your `index.md` file within the `contact` directory.
3. **Test the Form**:
    
    - After setting up the form, test it by submitting a sample entry to ensure everything works as expected.

Getform tutorial [here](https://blog.getform.io/how-to-add-a-contact-form-in-hexo/)
