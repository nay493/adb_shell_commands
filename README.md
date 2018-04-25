# adb_shell_commands

adb commands:
=============

$ adb devices 
	devices that are currently connected to my machine.
$ adb -s <device-1>	 uninstall <package ID of the app to be uninstalled>
EX: adb -s ZX1G324LHF uninstall hotspotsheild.android.vpn.debug

$ adb -s <device-1>	 uninstall <app to be Installed>
EX: adb -s ZX1G324LHF install abc.apk

adb -s ZX1G324LHF install -r -d abc.apk

where -r ==> reinstall & avoid exception if the app is already installed.
	  -d ==> saying that its ok to downgrade the app version(i.e. if v3 is already installed -d implies forcefully install v2/v1)
	  
$ adb shell dumpsys window windows | findstr/inquiry/grep Focus
	gives ID of the window i.e. on focus right now (i.e. visible on foreground)
	o/p-1

$adb shell dumpsys | findstr/inquiry/grep "DUMP OF SERVICE"

$ adb shell am start -c api.android.intent.LAUNCHER -a api.android.category.MAIN -n <o/p-1>
	launches window with ID o/p-1
$ adb shell am forcestop <o/p-1>
 am ==> application manager ?
$ adb shell pm clear <o/p-1>
 pm ==> package manager	
	
Log collecting from an app:

$ adb logcat -d	
	dumps all log in the log buffer at once at that instant 
$ adb logcat 
	continuous log as you perform some operation on mobile device, log gets added
	ctrl + c (To exit)
$ adb logcat -c
	-c clears the log buffer.
$ adb logcat > mylog.txt	
$ adb logcat | tee mylog.txt 2>&1
$ adb shell screencap </SDCARD/cap1.png>
	captures screenshot & saves it.
$ adb shell rm </SDCARD/cap1.png>
		removes screenshot captured
		
Note: adb shell ==> all the shell commands, I guess !! 	

$ adb push <push file to sd card path>
$ adb pull <pull file from sd card path>	
$ adb shell input text "srk"
$ adb shell input keyevent <3/4>
$ adb shell getprop
	gets properties in terms of key-value pair.
$ adb shell getprop wifi.interface
	
adb cheat sheet:
	https://devhints.io/adb
