# EZ-POV
Make POV images for ProffieOS.  
Uses ProffieOS POV Tools to create Point-Of-View Images that show when you swing the blade.

### Windows Requirements (Windows 10 at time of writing):  

Windows 10  
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

### MacOS Requirements (should also work on Linux):
- Install Homebrew https://treehouse.github.io/installation-guides/mac/homebrew
- Install netpbm (In Terminal, type "brew install netpbm").  


### Download the whole EZ-POV folder.  
- Click on the green "CODE" button on the main repo page https://github.com/NoSloppy/EZ-POV
- Choose to "Download ZIP".
- Once downloaded, highlight the .zip file, click "Extract" in pink in the window's top bar, then click "Extract All".
- Click "Browse" and choose somewhere, like your Desktop. Then click "Next".
- Inside EZ-POV-master is an EZ-POV folder. That is the working directory from here on out.

### Make POV files

- Get a .png image you want to convert and place it in the EZ-POV folder (you can try the Star Wars logo in the download).
There should be no spaces in your source filename.png. (Simple, single color images work best at the moment)
- Windows: Doubleclick "create_POV_data_files-Win.bat"  
    Mac: Doubleclick "create_POV_data_files-Mac"
- The source filename will be used to generate the output files.
- Check out resulting *preview.png, where *is your original filename. It should look windshieldwiper warped.
- Move the new *data.h file into ProffieOS/styles
    - If you processed a Single Color file, use the resulting *SC_POV_data.h file.
    - If Full Color source file, then use *FC_POV-data.h file.
- Edit ProffieOS/styles/pov.h. Change the #include on line 16 to be your new filename. Save.
- Then you just use the style in a preset::
```
{ "Font", "tracks/track.wav",
   &style_pov, 
  "my_pov"},
  ```

*NOTE* Each time you make a new POV image, you must first clear out any existing .png files from the EZ-POV folder.

