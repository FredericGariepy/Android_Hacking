# Frida Setup and Usage Tutorial for Android Emulator

### Find adb location
```cmd
C:\>dir adb.exe /s /p
```
### check for AVD 
```cmd
C:\your path to \Android\Sdk\platform-tools>.\adb.exe devices
List of devices attached
emulator-5554   device
```
### Verify Device Architecture
```cmd
adb shell getprop ro.product.cpu.abi
x86_64 <- for my AVD
```

### Get frida-server
device architecture: **x86\_64**. Use frida-server for **android-x86\_64**

Go to https://github.com/frida/frida/releases \
Get frida-server-17.2.11-android-x86_64.xz \
unzip

### Push Frida Server to Device
```cmd
.\adb.exe push C:\Users\BlueT\Downloads\fridaserver\frida-server-17.2.11-android-x86_64 /data/local/tmp/frida-server
C:\Users\BlueT\Downloads\fridaserver\frida-server...0 skipped. 224.8 MB/s (110700632 bytes in 0.470s)
```
### Setup Frida Server on Device
```cmd
C:\Users\BlueT\AppData\Local\Android\Sdk\platform-tools>.\adb.exe shell
emu64xa:/ $ ls -l /data/local/tmp/frida-server
-rw-rw-rw- 1 shell shell 110700632 2025-07-14 21:29 /data/local/tmp/frida-server
```
Grant Root with Majisk on AVD and run frida
```cmd
1|emu64xa:/ $ su
emu64xa:/ # chmod 755 /data/local/tmp/frida-server
emu64xa:/ # /data/local/tmp/frida-server &
[1] 15516
emu64xa:/ # ps | grep frida
root         15516 15479   10937912   2400 do_sys_poll         0 S frida-server
```

## ON SEPERATE TERMINAL
```cmd
C:\Users\BlueT>dir C:\*frida.exe /s /p
 Volume in drive C has no label.
 Volume Serial Number is B034-1DE5

 Directory of C:\Users\BlueT\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.11_qbz5n2kfra8p0\LocalCache\local-packages\Python311\Scripts

06/02/2025  08:34 PM           108,463 frida.exe
               1 File(s)        108,463 bytes

C:\Users\BlueT\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.11_qbz5n2kfra8p0\LocalCache\local-packages\Python311\Scripts>.\frida-ps.exe -U
  PID  Name
... stuff ...

Find the target app

emu64xa:/ # pm list packages
or

C:\Users\BlueT\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.11_qbz5n2kfra8p0\LocalCache\local-packages\Python311\Scripts>.\frida-ps.exe -U -a
  PID  Name               Identifier
-----  -----------------  ---------------------------------------
20088  Chrome             com.android.chrome
16432  Google             com.google.android.googlequicksearchbox
16432  Google             com.google.android.googlequicksearchbox
20954  Google Play Store  com.android.vending
17492  Messages           com.google.android.apps.messaging
20362  Personal Safety    com.google.android.apps.safetyhub
19189  Photos             com.google.android.apps.photos
16007  SIM Toolkit        com.android.stk
20115  Settings           com.android.settings
20837  TGNG               com.gloriousduck.tgng
16820  Test DPC           com.afwsamples.testdpc
16820  Test DPC           com.afwsamples.testdpc


20837  TGNG               com.gloriousduck.tgng # is the target

C:\Users\BlueT\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.11_qbz5n2kfra8p0\LocalCache\local-packages\Python311\Scripts>frida -U -p 20837
     ____
    / _  |   Frida 17.0.7 - A world-class dynamic instrumentation toolkit
   | (_| |
    > _  |   Commands:
   /_/ |_|       help      -> Displays the help system
   . . . .       object?   -> Display information about 'object'
   . . . .       exit/quit -> Exit
   . . . .
   . . . .   More info at https://frida.re/docs/home/
   . . . .
   . . . .   Connected to Android Emulator 5554 (id=emulator-5554)

[Android Emulator 5554::PID::20837 ]->
```
