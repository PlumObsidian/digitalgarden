---
{"dg-publish":true,"permalink":"/windows-11/clear-and-reset-quick-access-folders-in-command-prompt/","tags":["windows11","wsl"]}
---


## Clear and Reset Quick Access Folders in Command Prompt

  
1 Open [**Windows Terminal**](https://www.elevenforum.com/t/open-windows-terminal-in-windows-11.464/), and select **Command Prompt**.  
  
2 Copy and paste the command below into the command prompt, and press Enter. (see screenshot below)  
``` 
del /f /s /q /a "%AppData%\Microsoft\Windows\Recent\AutomaticDestinations\f01b4d95cf55d32a.automaticDestinations-ms"
```
