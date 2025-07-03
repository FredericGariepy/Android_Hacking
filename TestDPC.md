## 1. Get Test DPC
- https://github.com/googlesamples/android-testdpc/
- https://play.google.com/store/apps/details?id=com.afwsamples.testdpc

## 2. Set work profile..
![image](https://github.com/user-attachments/assets/51f3104b-b52f-4329-8d12-0638f63d2d54)



## 3. switch user.
Continue with Android UI to switch users (swipe down to user icon).

Make other users in terminal
1. `su`, get root with Majisk
2. pm create-user WorkUser
```
Success: created user id <id number>
emu64xa:/ #
```
3. go to profile, check profile
  List all users
    1. `pm list users`
    2. `am get-current-user`
```
C:\User\AppData\Local\Android\Sdk\platform-tools>.\adb.exe shell
emu64xa:/ $ pm list users
Users:
        UserInfo{0:Owner:4c13} running
        UserInfo{10:Work profile:1070} running
emu64xa:/ $ am get-current-user
0
emu64xa:/ $ exit

C:\Users\BlueT\AppData\Local\Android\Sdk\platform-tools>.\adb.exe shell
emu64xa:/ $ am get-current user
Unknown command: get-current
255|emu64xa:/ $ am get-current-user
11
emu64xa:/ $
```
