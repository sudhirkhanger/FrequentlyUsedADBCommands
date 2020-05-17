# FrequentlyUsedADBCommands

## Possible ways to move database to sdcard

    adb shell "run-as com.sudhirkhanger.app.stockhawk chmod 666 /data/data/com.sudhirkhanger.app.stockhawk/databases/quoteDatabase.db"
    
    adb pull /data/data/com.sudhirkhanger.app.stockhawk/databases/quoteDatabase.db .
    
    adb shell "run-as com.sudhirkhanger.app.stockhawk chmod 600 /data/data/com.sudhirkhanger.app.stockhawk/databases/quoteDatabase.db"
        
    adb shell
    run-as com.sudhirkhanger.app.stockhawk
    chmod 666 databases/quoteDatabase.db
    cp /data/data/com.sudhirkhanger.app.stockhawk/databases/quoteDatabase.db /sdcard/
    chmod 600 databases/quoteDatabase.db
    exit
    exit
    
    adb shell "run-as com.sudhirkhanger.app.stockhawk cp /data/data/com.sudhirkhanger.app.stockhawk/databases/quoteDatabase.db /sdcard/"
    exit
    exit
	
	adb shell "run-as applicationId cp /data/data/applicationId/files/default.realm /sdcard/" && adb pull /sdcard/default.realm ~/Downloads
	adb shell "run-as applicationId cp /data/data/applicationId/files/default.realm /sdcard/" && adb pull /sdcard/default.realm ~/Downloads/realm_$(date +%Y-%m-%d_%H-%M-%S).realm

## Copy a file from sdcard to current folder

    adb pull /sdcard/somefile.db .

## Clear App data

    adb shell pm clear com.sudhirkhanger.app.someapp

## Remove a package

    adb uninstall com.sudhirkhanger.app.someapp

## LCD Density hack

    adb shell getprop ro.sf.lcd_density
    adb shell wm density 280

## Attach emulator device

	adb -d forward tcp:5601 tcp:5601 //when connected with one device via usb
	adb -s 192.168.1.33:5555 forward tcp:5601 tcp:5601 //when you want to connect with a specific device

## Push an apk to the device

	adb install my-app.apk
	adb -s emulator-5554 my-app.apk

## Clean Statusbar

	adb shell settings put global sysui_demo_allowed 1
	
	// display time 12:00
	adb shell am broadcast -a com.android.systemui.demo -e command clock -e hhmm 1200

	// Display full mobile data without type
	adb shell am broadcast -a com.android.systemui.demo -e command network -e mobile show -e level 4 -e datatype false
	
	// Hide notifications
	adb shell am broadcast -a com.android.systemui.demo -e command notifications -e visible false
	
	// Show full battery but not in charging state
	adb shell am broadcast -a com.android.systemui.demo -e command battery -e plugged false -e level 100
	
	// display time 12:00
	adb shell am broadcast -a com.android.systemui.demo -e command clock -e hhmm 1200
	
	// Display full mobile data without type
	adb shell am broadcast -a com.android.systemui.demo -e command network -e mobile show -e level 4 -e datatype false
	
	// Hide notifications
	adb shell am broadcast -a com.android.systemui.demo -e command notifications -e visible false
	
	// Show full battery but not in charging state
	adb shell am broadcast -a com.android.systemui.demo -e command battery -e plugged false -e level 100

	adb shell am broadcast -a com.android.systemui.demo -e command exit
	
[Clean your status bar like a pro!](https://android.jlelse.eu/clean-your-status-bar-like-a-pro-76c89a1e2c2f)


## Running Activites

	// check ACTIVITY MANAGER ACTIVITIES (dumpsys activity activities) Running activities section
	adb shell dumpsys activity
	adb shell dumpsys activity activities | sed -En -e '/Stack #/p' -e '/Running activities/,/Run #0/p'

## Multiple devices

	adb -s <device-id> // adb devices
