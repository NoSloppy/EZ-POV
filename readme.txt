# create_POV_data_files (script)
Use ProffieOS POV Tools to create Point-Of-View images that show when you swing the blade.  
Under the hood:  
pnmtorle - Converts a full-color image to hex data to be included in the code.  
pgmtorle - Converts a single-color image to hex data to be included in the code.  
pnmwindshieldwiper - Scales the image and bends it so that it will work on a swinging blade.  
pnmquantizedtorle - Quantizes images to 8bit 256 colors to balance using color images and not taking up too much memory.  

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

### Make POV files

- Put a .png image you want to convert into the pov_tools folder.  
If there are any spaces in your filenames, the script will change them to underscores for you before processing.
If you have no images but want to try the sample Star Wars logo .png, run the script anyway and it will download and process it for you :)  
Each time you make a new POV image, you must first clear out any existing .png files from the pov_tools folder.  
The script will present a delete option for the previous preview.png and data files. 

- Windows: Doubleclick "create_POV_data_files-Win.bat"  
    (If Microsoft Defender pops up a warning, click "More Info" then "Run anyway")  
    Mac or Linux: Doubleclick "create_POV_data_files"  
    
- Type the name of your image (including the .png extension)  
- Choose a sizing option from the list. 3 preset sizes plus Height entry only and Custom size are the options.  
(Height should probably be the blade length)
- Check the resulting preview.png in the pov_tools folder. It should look windshieldwiper warped.
- The image data files are written directly to the ProffieOS/styles folder.
- To use the POV data file for a blade style, first tell the OS which one  
with the following line added to your config file in the CONFIG_TOP section:  
`#define POV_INCLUDE_FILE "dataFileNameHere.h"`

- If you used a Single Color source file, use the resulting image_pgm.h file.  
If you used a Full Color source file, then use the resulting image.h file.  
If you used a Full Color source file, memory use might be less choosiing the image_8bit.h file.  

- Then you just use the POV blade style in a preset::
```
{ "Font", "tracks/track.wav",
   &style_pov, 
  "my_pov"},
  ```

Swing the blade in a steady movement to see the image in the air. A long-exposure capture showcases the result best.
Enjoy!  (⌐■_■)
