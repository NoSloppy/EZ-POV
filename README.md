# EZ-POV
Make POV images for ProffieOS

ProffieOS POV Tools instructions using EZ-POV:
Create Point-Of-View Images that show when you swing the blade.

Windows (Windows 10 at time of writing):
Prettier post of Windows instructions here: 
https://crucible.hubbe.net/t/port-pov-tools-to-windows/1210/14


Requirements:
Windows 10
“Windows Subsystem for Linux”
Type “Turn Windows features on or off” into the windows search
Scroll down and enable it
Steps:
Get the Ubuntu App in the Microsoft Store (required for “bash” and other commands)
Get the EZ-POV tool at:
https://www.dropbox.com/sh/whhrieg6pp4nnaa/AACHYWQCtNUJIb-eAuDogqkja?dl=0
Put the EZ-POV folder somewhere, like Desktop.
This should include
- create_POV_data_files
- Makefile
- pgmtorle.cc
- pnmtorle.cc
- pnmwindshieldwiper.cc
- Star_Wars_Logo.png

Create a textfile (e.g. EZ-POV.txt) in that folder
Open it and put this line into it
Start powershell -noexit -command "bash create_POV_data_files"
Rename the file into a .bat-file (e.g. EZ-POV.bat)
This will be your executable file to start the script
This is a nifty trick courtesy of @NoSloppy used in his font-renaming tool
Get a .png-file you want to convert and also place it in that folder (you can try the Star Wars logo in the download)
If you were to execute the .bat-file it would now fail because of missing commands
Type “WSL” into the windows search and click that cheeky penguin image
Type “make” into
If you don’t already have it, the console will give you a hint on how to install it. Follow the instructions.
You will also need to install "g++", to do that follow steps 4-6 in this manual.
Type any of the three “pngtopnm”, “pnmscale” or "pnmtopng", and you should get a prompt to install “netpbm”. Follow the instructions.
Double-click your .bat-file
If everything was done correctly, powershell should open and execute the scripts.
You should get two .h-files and a preview image
Check out resulting *preview.png, where *is your original filename. It should look windshieldwiper warped.
Move the new *data.h file into ProffieOS/styles
    - If you processed a Single Color file, use the resulting *SC_POV_data.h file.
    - If Full Color source file, then use *FC_POV-data.h file.
Edit pov.h line 16 to your new filename.
Then you just use the style in a preset::

{ "Font", "tracks/track.wav",
   &style_pov, 
  "my_pov"},
Each time you make a new POV image, you must first clear out any existing .png files from that working POVimage folder (or whatever you named it.).


MacOS (should also work on Linux)

You'll need to install netpbm, and I suggest installing Homebrew before that. Google will get you there.

To create the POV image data files:

Download the EZ-POV.zip from here:
https://www.dropbox.com/sh/whhrieg6pp4nnaa/AACHYWQCtNUJIb-eAuDogqkja?dl=0

Move the EZ-POV folder somewhere to work with it.

1. No spaces in your source filename.png
2. Drop the source .png into the same POVimage folder.
3. Doubleclick create_POV_data_files
4. The source filename will be used to generate the output files.
5. Check out resulting *preview.png, where *is your original filename. It should look windshieldwiper warped.
6. Move the new *data.h file into ProffieOS/styles
    - If you processed a Single Color file, use the resulting *SC_POV_data.h file.
    - If Full Color source file, then use *FC_POV-data.h file.
7. Edit pov.h line 16 to your new filename.
8. Then you just use the style in a preset::

{ "Font", "tracks/track.wav",
   &style_pov, 
  "my_pov"},

Each time you make a new POV image, you must first clear out any existing .png files from that working POVimage folder (or whatever you named it.).
