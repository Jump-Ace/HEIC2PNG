# HEIC2PNG

 Automatically Convert And Resize .HEIC Files To .PNG
																												   
Jump_Ace presents, with thanks in large part to ChatGPT: https://chat.openai.com and ImageMagick: https://imagemagick.org

----------------
| HEIC2PNG 1.0 |
----------------

::What It Does::

Tired of manually converting HEIC files to PNGs manually every time you want to copy images from your iPhone?  Are they too large for what you need?  This script and app package may be for you!

The included Powershell scripts and ImageMagick app will allow you to copy image files from your iphone to the designated 'C:\Images' folder, convert all the included .HEIC files to PNG, resize them down around 75% of their original size and store them in the 'PNGs' subfolder.  You can then create a Scheduled Task in Windows to run one of the scripts automatically when you log in.


::How To Set It Up::

 - Open the Zip file with your favorite archive app (i.e. 7-zip) then:
 - Extract the 'Images - Desktop Shortcut' file to your desktop
 - Extract the 'Images' folder to the root of your C:\ drive
 - Extract the 'Scripts' folder to the root of your C:\ drive
 - Download ImageMagick select the appropriate verstion below:
	- x64 bit portable: https://imagemagick.org/archive/binaries/ImageMagick-7.1.1-15-portable-Q16-HDRI-x64.zip
	- x86 bit portable: https://imagemagick.org/archive/binaries/ImageMagick-7.1.1-15-portable-Q16-HDRI-x86.zip
	- Or choose any of their installers found here: https://imagemagick.org/script/download.php#windows
 - Create a new folder and name it 'Image-Magick' on your desktop
 - Extract all the files in the ImageMagick Zip file that you just downloaded, into the new 'Image-Magick' folder
 - Move the 'Image-Magick' folder to the 'C:\Images' directory
 - Open the Windows 'Task Scheduler' app
 - Click 'Create Basic Task' on the right
 - Type in any name you want and click Next
 - Select 'When I log on' and click Next
 - Select 'Start a program' and click Next
 - In the top 'Program/script:' field, type powershell.exe
 - In the 'Add arguements (optional):' field, type -F "C:\Scripts\MonitorImagesDirectory.ps1" and click Next
 - Be sure to click the 'Open the Properties dalog for this task when I click Finish' box, then click Finish
 - Be sure you are on the 'General' tab at the top, select the 'Run whether user is logged on or not'
 - Check the 'Run with highest privileges' box
 - Select 'Windows 10' in the 'Configure for:' dropdown menu and click OK
 - It should prompt you to enter the password of the windows account you are signed in with, type it in, then click OK


::How To Use It::

If the Scheduled Task is configured properly to point to the 'MonitorImagesDirectory.ps1' script upon login, all you have to do is drag and drop your .HEIC files from your iPhone to the included 'Images - Desktop Shortcut' shortcut folder that you copied to your desktop.  When it's finished, the script will remove the original .HEIC file(s) from the C:\Images directory and your PNG files will be numerically named inside the 'PNGs' subfolder ready for use.


::How It Works::

The 'MonitorImagesDirectory.ps1' file actively monitors the 'C:\Images' directory so when .HEIC files are copied into that directory, it will kick off the 'HEIC2PNG.ps1' script.  That script will use ImageMagick (the app is portable so no installagaion is necessary) to convert and resize the image file(s), save them in the 'PNGs' subfolder, name them numerically starting wtih '1.png' (then '2.png' and so on) and then delete the original .HEIC file in the 'C:\Images' "root" directory.
