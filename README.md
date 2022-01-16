# EZ-POV 
Uses ProffieOS POV Tools to create Point-Of-View images that show when you swing the blade.  
Under the hood:  
pnmtorle - Converts a full-color image to hex data to be included in the code.  
pgmtorle - Converts a single-color image to hex data to be included in the code.  
pnmwindshieldwiper - Scales the image and bends it so that it will work on a swinging blade.  

### Operating System Requirements:  
### Windows (Windows 10 at time of writing):  

Install Windows Subsystem for Linux  
- Get Ubuntu App in the Microsoft Store. (required for “bash” and other commands). Download but don't choose open once it finishes installing. 
https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab
- Type “Turn Windows features on or off” into the Windows search, open the top result, scroll down and enable "Windows Subsystem for Linux".
- Click "OK", then click "Reboot Now". 
- Open the Ubuntu app and wait while it says "Installing, this may take a few minutes...".
- Choose a username and password. Once you get a green prompt (should be username+computername), close the window.
- Type “WSL” into the windows search and click that cheeky penguin image.  

Install g++ and netpbm
- It goes without saying that you hit the return key after each of the following entries.
- In the command line window that opened, type "sudo apt-get update". Enter your password.
- When that finishes, type "sudo apt-get install build-essential gdb".
- Answer the question with "y".
- When that finishes, type "sudo apt install netpbm".
- Answer the question with "y".

### MacOS:
- Install Homebrew https://treehouse.github.io/installation-guides/mac/homebrew
- Install netpbm (In Terminal, type "brew install netpbm").  

### Linux
- Install netpbm http://netpbm.sourceforge.net/

---------------------------------------------------------------------------------------
### Download the whole EZ-POV folder.  
- Click on the green "CODE" button on the main repo page https://github.com/NoSloppy/EZ-POV
- Choose to "Download ZIP".
- Once downloaded, highlight the .zip file, click "Extract" in pink in the window's top bar, then click "Extract All".
- Click "Browse" and navigate to the 'ProffieOS/pov_tools' folder. Then click "Next".
- Inside EZ-POV-master is an EZ-POV folder. That is the working directory from here on out.

### Make POV files

- Put the .png image you want to convert into the EZ-POV folder. (Simple, single color images work best at the moment)  
There should be no spaces in your source filename.png.  
For an example, you can right-click and Save the sample Star Wars logo .png here:  
https://upload.wikimedia.org/wikipedia/commons/thumb/6/6c/Star_Wars_Logo.svg/1024px-Star_Wars_Logo.svg.png  

*NOTE* **- Each time you make a new POV image, you must first clear out any existing .png files from the EZ-POV folder.** 
- Windows: Double click "create_POV_data_files-Win.bat"  
    (If Microsoft Defender pops up a warning, click "More Info" then "Run anyway")  
    Mac or Linux: Double click "create_POV_data_files"  
    Optionally, you can use command line tools of course. 'cd' to the 'pov_tools' directory and type 'make'.
- Check the resulting *preview.png, where * is your original filename. It should look windshieldwiper warped.
- The required data files *_POV_data.h have been written to the ProffieOS/styles folder.
- Add the following lines to your config file, the same way a prop file is setup: (Example filename is used here)
```
#ifdef CONFIG_POV
#include "../styles/1024px-Star_Wars_Logo.svg_SC_POV_data.h"
#endif
```
- If you processed a Single Color source file, use the resulting *_SC_POV_data.h file.
- If you processed a Full Color source file, then use the resulting *_FC_POV_data.h file.
- Then you just use the POV blade style in a preset::
```
{ "Font", "tracks/track.wav",
   &style_pov, 
  "my_pov"},
  ```

Swing the blade in a steady movement to see the image in the air. A long-exposure capture showcases the result best.
Enjoy!  (⌐■_■)


