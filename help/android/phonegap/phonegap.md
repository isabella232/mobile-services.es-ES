---
description: Este complemento le permite enviar llamadas de AppMeasurement de Android desde el proyecto de PhoneGap.
keywords: android, biblioteca, mobile, móvil, sdk
solution: Experience Cloud Services,Analytics
title: Información general del complemento PhoneGap
topic-fix: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
exl-id: ecd756ca-e333-4d28-bd1e-a75ffc6ebe22
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 97%

---

# Información general del complemento PhoneGap {#phonegap-plug-in}

Este complemento le permite enviar llamadas de AppMeasurement de Android desde el proyecto de PhoneGap. Para crear un proyecto de PhoneGap, consulte [PhoneGap](https://helpx.adobe.com/es/experience-manager/6-4/mobile/using/phonegap.html).

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).


## Instalación del complemento utilizando npm {#section_43229E57C16944C0B51531CB92089189}

Ejecute el siguiente comando:

```java
cordova plugin add adobe-mobile-services
```

## Instalación manual del complemento  {#section_EA1FD59C484D44878AB509954DEE6037}

## Incluir el complemento

1. Arrastre el archivo `ADBMobile_PhoneGap.java` a la carpeta `src`.

   Para mover este archivo, haga clic en **[!UICONTROL Aceptar]**.

1. Arrastre el archivo `ADB_Helper.js` a la carpeta que contenga el archivo `index.html`

   Para mover este archivo, haga clic en **[!UICONTROL Aceptar]**.

1. En la carpeta `res/xml`, abra el archivo `config.xml` y registre un nuevo complemento agregando lo siguiente:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   Por ejemplo, si su paquete se llama `com.example.phonegaptest`, el valor `android-package` sería el siguiente:

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Incluir la biblioteca de AppMeasurement

1. Para descargar la biblioteca de AppMeasurement, consulte [Obtener el SDK](/help/android/getting-started/dev-qs.md).
1. Arrastre el archivo `adobeMobileLibrary.jar` a la carpeta `src`.

   Para mover este archivo, haga clic en **[!UICONTROL Aceptar]**.

1. Haga clic con el botón derecho en el `adobeMobileLibrary.jar` y seleccione **[!UICONTROL Agregar como biblioteca]**.
1. En función de los requisitos de su proyecto, introduzca el nombre, nivel y ubicación de la biblioteca.
1. Arrastre el archivo `ADBMobileConfig.json` a su carpeta `assets` en la raíz de la aplicación.
1. Confirme que ha seleccionado la raíz de la aplicación y **no** una aplicación dentro de una aplicación.

   Para mover este archivo, haga clic en **[!UICONTROL Aceptar]**.

## Añadir permisos de aplicaciones

La biblioteca AppMeasurement requiere los siguientes permisos para enviar datos y registrar llamadas de seguimiento sin conexión:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Para agregar estos permisos, agregue las siguientes líneas al archivo `AndroidManifest.xml`, que se encuentra en el directorio del proyecto de la aplicación:

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Para habilitar la mensajería en la aplicación:

Actualice AndroidManifest.xml para declarar la actividad de pantalla completa y habilitar el controlador de notificación de mensajes:

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

Si selecciona el diseño modal al crear un mensaje en Adobe Mobile Services, elija uno de los temas siguientes:

* `Theme.Translucent.NoTitleBar.Fullscreen`
* `Theme.Translucent.NoTitleBar`
* `Theme.Translucent`

Por ejemplo:

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Implementación del seguimiento personalizado {#section_FD102B3CDAA4492FB04E56BF17E28663}

En los archivos `html`, añada lo siguiente a la etiqueta `<head>` donde quiera utilizar el seguimiento:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```
