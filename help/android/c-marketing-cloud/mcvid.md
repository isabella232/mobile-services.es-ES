---
description: El servicio de identidad de Adobe Experience Platform proporciona un ID de visitante universal en todas las soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-description: El servicio de identidad de Adobe Experience Platform proporciona un ID de visitante universal en todas las soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-title: Experience Cloud ID configuration
solution: Marketing Cloud,Analytics
title: Configuración de ID de Experience Cloud
topic: Desarrollador e implementación
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID configuration {#experience-cloud-id-configuration}

El servicio de identidad de Adobe Experience Platform proporciona un ID de visitante universal en todas las soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.

>[!TIP]
>
>You do not need to populate this ID unless you are using the Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.3 o posterior del SDK.

Para habilitar el Experience Cloud ID:

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* IntelliJ IDEA o Eclipse en la implementación [principal y el ciclo vital](/help/android/getting-started/dev-qs.md).

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Compruebe que el `ADBMobileConfig.json` archivo contiene el `marketingCloudorg`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Los ID de organización de Experience Cloud permiten identificar de forma exclusiva cada empresa cliente en Adobe Experience Cloud y tienen un valor similar a este:

   ```js
   016D5C175213CCA80A490D05@AdobeOrg`
   ```

   >[!IMPORTANT]
   >
   >You must include .`@AdobeOrg`

   If these IDs are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obtener más información, consulte [Antes de comenzar](/help/android/getting-started/requirements.md).

Tras completar la configuración, se genera un Experience Cloud ID que se incluye en todas las visitas. Otros ID, como los ID personalizados y los generados automáticamente, se siguen enviando con cada visita.
