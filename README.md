# Generate-8bit-GFX-Font
**Easy way to generate your own 8bit GFX Font from free TrueType fonts**

Source: https://github.com/Bodmer/Adafruit-GFX-Library - using modified Adafruit fontconvert done by Bodmer.

I needed some speical chars for German and French glyphs (Umlaute and éè etc.) for Bodmer´s TFT_eSPI. I was searching hours to find a working and simple mehtod to generate a 8bit GFX font from a free .ttf file. (https://fonts.google.com)

This step-by-step tutorial has been done on a Linux system. I tried to do it first with the M1/M2 Macs but it generated too much errors so (lazy me) I decicded to do it on a OrangePi that was laying around.

**Step 1**

REQUIRES FREETYPE LIBRARY, so install it first on your Pi:

`sudo apt-get install libfreetype6-dev`

If you run into errors, consult this side: https://techoverflow.net/2019/06/11/how-to-fix-ft2build-h-no-such-file-or-directory/

**Step 2**

Copy files to your Pi. I used FileZilla to copy all files of this Repository to /usr/bin/fontconvertbodmer/

a.) download .zip from this side (green button "Code")  
b.) unzip *-master.zip file  
c.) create directory fontconvertbodmer in /usr/bin  
d.) copy files to /user/bin/fontconvertbodmer/  

Your structure should look like /usr/bin/fontconvertbodmer/fontconvert/fontconvert.c

**Step 3**

Generate fontconvert executable. (my working one for Armbian is also in the directory, you might jump to Step 4)

`cd /user/bin/fontconvertbodmer/fontconvert` 
`make -f Makefile'

**Step 4**

Convert any font with your new fontconvert executable. Try it with the Nunito-Italic.ttf from Google fonts.

Converting logic is: ./fontconvert [your_ttf_file] [fontsize] [last ascii sign] > [generated .h file]

`./fontconvert /user/bin/fontconvertbodmer/fontconvert/Nunito-Italic.ttf 12 255 > Nunito-Italic128b.h`

**Step 5**

Use this generated header file like any other freefont file.  
:smile:

