Goal: fake GPS in app and capture tile in Antartica. 
## 1. In AVD, download target app: TGNG
## 2. Open target app, and find package name

```cmd
C:\Users\<yourname>\AppData\Local\Android\Sdk\platform-tools>.\adb.exe shell dumpsys window | find "mCurrentFocus"
  mCurrentFocus=Window{1df1239 u0 com.gloriousduck.tgng/com.gloriousduck.tgng.MainActivity}
```

continue later...
