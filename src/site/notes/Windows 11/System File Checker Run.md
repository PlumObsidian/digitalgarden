---
{"dg-publish":true,"permalink":"/windows-11/system-file-checker-run/","tags":["windows11","howto","system"]}
---

To run the Windows System File Checker (SFC) utility, open Command Prompt as an administrator, type `sfc /scannow`, and press Enter. This command will scan for and attempt to repair any corrupted or missing system files. 

Here's a more detailed breakdown:

- **Open Command Prompt as Administrator:**
    
    - Press the Windows key + X 
    - Select "Command Prompt (Admin)" from the menu 
    - Alternatively, search for "cmd" in the search bar, right-click on "Command Prompt", and select "Run as administrator". 
    
- **Run the SFC Scan:**
    
    - In the Command Prompt window, type `sfc /scannow`. 
    - Press Enter. 
    
- **Wait for the Scan to Complete:**
    
    - The System File Checker will verify the integrity of protected operating system files. 
    - If it finds any corrupted or missing files, it will attempt to repair them automatically. 
    
- **Check for Results:**
    
    - Once the scan is complete, you'll see a message indicating whether any problems were found and corrected. 
    - If files were repaired, restart your computer. 
    
- **Repeat the Process:**
    
    - If the original problem persists, repeat the process or try other troubleshooting steps.