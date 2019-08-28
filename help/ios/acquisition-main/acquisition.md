---
description: Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde el App Store de Apple después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.
seo-description: Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde el App Store de Apple después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.
seo-title: Adquisición de aplicación móvil
solution: Marketing Cloud, Analytics
title: Adquisición de aplicación móvil
topic: Desarrollador e implementación
uuid: 5 fece 619-e 4 b 8-4 d 06-9250-dcb 66 fa 32 ce 0
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Mobile app acquisition {#mobile-app-acquisition}

Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde el App Store de Apple después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.

Para utilizar Adquisición **necesita** la versión 4.1 o posterior del SDK.

Los vínculos de Acquisition se deben crear en Adobe Mobile Services. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

La información de esta sección permite al SDK enviar datos de adquisición desde un vínculo de adquisición.

## Tracking mobile app acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración al proyecto* en [Implementación principal y Ciclo vital](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >Si envía datos a varios grupos de informes, utilice la configuración de adquisición (servidor de adquisición y appid) de la aplicación asociada al primer grupo de informes de su lista de ID de grupos de informes.

   `acquisition` La configuración los genera Adobe Mobile Services y no debe cambiarse. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/ios/getting-started/requirements.md).

Una vez habilitada esta configuración y después del primer inicio de la aplicación, los datos de adquisición se envían automáticamente con la llamada inicial del ciclo vital.

>[!CAUTION]
>
>`referrerTimeout` debe establecerse en un valor superior a 0 para habilitar la adquisición de aplicación.

## Activación de la aplicación de iOS para los vínculos universales

Si utiliza vínculos universales en su aplicación, agregue el dominio Vínculos de marketing de Adobe a la lista Dominios asociados para su aplicación.

En Xcode, para agregar su dominio de Vínculos de marketing de Adobe a la lista Dominios asociados:

1. Vaya a su objetivo de proyecto y haga clic en la **[!UICONTROL ficha Capacidades]** .
2. Desplácese hacia abajo hasta **[!UICONTROL la sección Dominios]** asociados y configúrela.
3. Agregue una entrada en la lista **[!UICONTROL Dominios]** para su dominio Vínculos de marketing desde la URL de vínculos de marketing.

Su entrada tendrá un aspecto similar `applinks:5848561889a02a6996aea62b.c00.adobe.com`.