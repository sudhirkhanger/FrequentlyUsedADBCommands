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
	abd -s 192.168.1.33:5555 forward tcp:5601 tcp:5601 //when you want to connect with a specific device
