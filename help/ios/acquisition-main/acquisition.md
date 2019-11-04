---
description: Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde el App Store de Apple después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.
seo-description: Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde el App Store de Apple después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.
seo-title: Adquisición de aplicación móvil
solution: Experience Cloud,Analytics
title: Adquisición de aplicación móvil
topic: Desarrollador e implementación
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Adquisición de aplicación móvil {#mobile-app-acquisition}

Los vínculos de adquisición con códigos de seguimiento únicos se pueden generar en Adobe Mobile Services. Cuando un usuario descarga y ejecuta una aplicación desde el App Store de Apple después de hacer clic en el vínculo generado, el SDK recopila automáticamente y envía los datos de adquisición a Adobe Mobile Services.

Para utilizar Adquisición **necesita** la versión 4.1 o posterior del SDK.

Los vínculos de Acquisition se deben crear en Adobe Mobile Services. Para obtener más información, consulte [Adquisición](/help/using/acquisition-main/acquisition-main.md).

La información de esta sección permite al SDK enviar datos de adquisición desde un vínculo de adquisición.

## Seguimiento de la adquisición de aplicación móvil {#section_CEA30C652AC8470784B8054E299B80FA}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Compruebe que el archivo `ADBMobileConfig.json` contiene la configuración de adquisición necesaria:

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
   >Si está enviando datos a varios grupos de informes, utilice la configuración de adquisición (servidor de adquisición y appid) de la aplicación asociada al primer grupo en su lista de ID de grupos de informes.

   La configuración de `acquisition` la genera Adobe Mobile Services y no debería cambiarse. Para obtener más información sobre cómo descargar un archivo `ADBMobileConfig.json` personalizado con los ajustes de `acquisition` preconfigurados, consulte [Antes de comenzar](/help/ios/getting-started/requirements.md).

Una vez habilitada esta configuración y después del primer inicio de la aplicación, los datos de adquisición se envían automáticamente con la llamada inicial del ciclo vital.

>[!CAUTION]
>
>`referrerTimeout` debe estar establecido en un valor mayor que 0 para habilitar la adquisición de aplicación.

## Activación de la aplicación de iOS para vínculos universales

Si utiliza vínculos universales en la aplicación, agregue su dominio de vínculos de marketing de Adobe a la lista Dominios asociados de la aplicación.

En Xcode, para agregar el dominio Vínculos de marketing de Adobe a la lista Dominios asociados:

1. Vaya al destino del proyecto y haga clic en la pestaña **[!UICONTROL Funcionalidades]**.
2. Vaya a la sección **[!UICONTROL Dominios asociados]** y actívela.
3. Agregue una entrada en la lista **[!UICONTROL Dominios]** del dominio Vínculos de marketing dusando la dirección URL.

La entrada debería tener el siguiente aspecto: `applinks:5848561889a02a6996aea62b.c00.adobe.com`.