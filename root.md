## 1. Install Android Studio
https://developer.android.com/studio/install

## 2. Make an Android Virtual Device (AVD)
- https://developer.android.com/studio/run/managing-avds

Then, Run an AVD

## 3. Use Android Debug Bridge (adb) to get shell into AVD
- https://developer.android.com/tools/adb.exe 

Find adb.exe path
```cmd

C:\>dir adb.exe /s /p
...

 Directory of C:\Users\<yourname>\AppData\Local\Android\Sdk\platform-tools

11/25/2024  01:49 AM         5,969,000 adb.exe
               1 File(s)      5,969,000 bytes

```
At the path, run adb - check for device, make sure thing are cool: 
```cmd
C:\Users\<yourname>\AppData\Local\Android\Sdk\platform-tools>.\adb.exe devices
List of devices attached
emulator-5554   device

C:\Users\<yourname>\AppData\Local\Android\Sdk\platform-tools>.\adb.exe shell
emu64xa:/ $ whoami
shell
emu64xa:/ $
```
## 4. Get root with majisk through rootAVD

- https://github.com/newbit1/rootAVD \
Script to root AVDs running with QEMU Emulator from Android Studio

find your rootAVD folder
```cmd
C:\>dir rootAVD /s /p
```
Go to path and run rootAVD to get example command. Execute it.
```cmd
C:\Users\<yourname>\rootAVD>.\rootAVD.bat`
...
rootAVD.bat system-images\android-35\google_apis_playstore\x86_64\ramdisk.img
```
Follow output steps. AVD restart. \
After restart, on the AVD find and open majisk.

Enter the shell with adb
```cmd
C:\Users\<yourname>\AppData\Local\Android\Sdk\platform-tools>.\adb.exe shell
```
Grant root on AVD \
![Grant Root](https://github.com/user-attachments/assets/3da9d796-314d-4aad-a546-8d1ad0a65afa)
```cmd
emu64xa:/ $ su
emu64xa:/ # whoami
root
emu64xa:/ #
```
