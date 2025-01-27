---
{"dg-publish":true,"permalink":"/linux-applications-and-cheat-sheets/sublime-text-editor/adding-spellcheck-to-sublime-text-editor/","tags":["sublime","text","editor","howto"]}
---

To add spell check to Sublime Text, you can: 

1. Open the Preferences menu
2. Select Settings
3. Select User
4. Add the code `{"spell_check": true}`
5. Save the file

You can also enable spell checking for specific file types, like Markdown. To do this, you can: 

1. Open or create a file of the desired type
2. Go to Preferences > Settings > More > Syntax Specific > User
3. Add the code `{"spell_check": true}`

You can also add additional dictionaries to Sublime Text. To do this, you can: 

- Convert the dictionary to UTF-8
- Install the dictionary in a package, like Packages/User
- Select the dictionary from the View/Dictionary menu
- Use the OpenOffice.org Extension List to get additional dictionaries
- Use the [Sublime Text Package Control](https://packagecontrol.io/packages/Dictionary) to install the Dictionary plugin