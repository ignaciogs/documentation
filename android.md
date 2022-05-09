
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

<br/><br/>
Conectar eld adb por wifi
```console
adb tcpip 1234
Adb connect xxx.xxx.xxx.xxx:1234
```

<br/><br/>
Consultar el SHA1 ó SHA256 de una firma (KEYTOOL)
```console
keytool -list -v -keystore fichero_firma.jks -alias nombre_alias_dentro_del_fichero_de_firma

#Ejemplo para inditex
keytool -list -v -keystore inditex_preproduction.jks -alias inditex_preproduction

#Versión release
keytool -exportcert -list -v \ -alias <your-key-name> -keystore <path-to-production-keystore>

@Versión debug usando el fichero de firma por defecto
keytool -exportcert -list -v -alias androiddebugkey -keystore ~/.android/debug.keystore
```
<br/><br/>
Consultar las alarmas que estan activas en un dispositivo
```console
adb shell dumpsys alarm
```

<br/><br/>
Probar una aplicación con Monkey
```console
adb shell monkey -p com.mypackagename --throttle 500 -v 10000
```
