---
description: El servicio de identidad de Adobe Experience Platform proporciona un ID de visitante universal en las soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-description: El servicio de identidad de Adobe Experience Platform proporciona un ID de visitante universal en las soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-title: Experience Cloud ID
solution: Marketing Cloud, Analytics
title: Experience Cloud ID
topic: Desarrollador e implementación
uuid: 13628 ea 8-3 cd 4-4 cfc -8 ff 6-722 c 33 f 7813 a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

El servicio de identidad de Adobe Experience Platform proporciona un ID de visitante universal en las soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.

>[!TIP]
>
>No necesita rellenar el ID de Experience Cloud a menos que utilice el servicio de identidad de Adobe Experience Platform. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**Requiere el SDK versión 4.3 o posterior**

## Habilitar el ID de Experience Cloud {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración al proyecto* en [Implementación principal y Ciclo vital](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Compruebe que `ADBMobileConfig.json` los archivos contengan `marketingCloud``org`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Los ID de organización de Experience Cloud permiten identificar de forma exclusiva cada empresa cliente en Adobe Experience Cloud y tienen un valor similar a este: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Debe incluir `@AdobeOrg`.

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obtener más información, consulte [Configuración JSON de adbmobile](/help/ios/getting-started/requirements.md).

Tras completar la configuración, se genera un Experience Cloud ID que se incluye en todas las visitas. Otros ID de visitante, como los ID personalizados y los generados automáticamente, se siguen enviando con cada visita.
