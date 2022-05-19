
# Android

* [ADB](#adb)
* [Plugins Android Studio](#plugins)
* [Expresiones regulares](#regex)

## <a name="adb">ADB</a>

###### Resetear el modo debugger
```console
adb shell am clear-debug-app
```

###### Enviar una notificación por terminal
```console
adb shell am broadcast -a com.google.android.c2dm.intent.RECEIVE -n com.mypackagename/com.google.android.gms.gcm.GcmReceiver --es "data.alert" "foo"

```

###### Conectar eld adb por wifi
```console
adb tcpip 1234
Adb connect xxx.xxx.xxx.xxx:1234
```

###### Consultar el SHA1 ó SHA256 de una firma (KEYTOOL)
```console
keytool -list -v -keystore fichero_firma.jks -alias nombre_alias_dentro_del_fichero_de_firma

#Ejemplo para inditex
keytool -list -v -keystore inditex_preproduction.jks -alias inditex_preproduction

#Versión release
keytool -exportcert -list -v \ -alias <your-key-name> -keystore <path-to-production-keystore>

@Versión debug usando el fichero de firma por defecto
keytool -exportcert -list -v -alias androiddebugkey -keystore ~/.android/debug.keystore
```
###### Consultar las alarmas que estan activas en un dispositivo
```console
adb shell dumpsys alarm
```

###### Probar una aplicación con Monkey
```console
adb shell monkey -p com.mypackagename --throttle 500 -v 10000
```

## <a name="plugins">Plugins Android Studio</a>
* [JSON To Kotlin Class](https://plugins.jetbrains.com/plugin/9960-json-to-kotlin-class-jsontokotlinclass-) Convierte un JSON en POJO
* [ADB Idea](https://plugins.jetbrains.com/plugin/7380-adb-idea) Accesos rápidos para resetear, limpiar datos, debuguear, etc..
* [Rainbow Brackets](https://plugins.jetbrains.com/plugin/10080-rainbow-brackets) Colorea para su fácil identificación caracteres como "{", "\[", "(", etc...
* [CodeTogether](https://plugins.jetbrains.com/plugin/14225-codetogether) Permite hacer pair programing con dos o más personas
* [Key Promoter X](https://plugins.jetbrains.com/plugin/9792-key-promoter-x) Mustra una alerta con el atajo de teclado correspondiente a la acción que se ha realizado con el ratón, para ir aprendiendo los atajos

## <a name="regex">Expresiones regulares</a>
Expresiones regulares interesantes para buscar en el AS
| Expresión | Descipción |
|----------|------------|
| . | Cualquier caracter |
| * | Repite indefinidamente el caracter que tiene antes |

Ejemplos útiles
| Expresión | Significado |
|----------|------------|
| sc.*en | Devolverá todos los textos que empiecen por "sc" y terminen por "en", como po ejemplo "screen" |
