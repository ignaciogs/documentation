
# Android

* [ADB](#adb)

## <a name="adb">ADB</a>

Resetear el modo debugger
```console
adb shell am clear-debug-app
```

<br/><br/>
Enviar una notificación por terminal
```console
adb shell am broadcast -a com.google.android.c2dm.intent.RECEIVE -n com.mypackagename/com.google.android.gms.gcm.GcmReceiver --es "data.alert" "foo"

```
