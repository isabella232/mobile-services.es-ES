---
description: The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-description: The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-title: Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Experience Cloud ID
topic: Desarrollador e implementación
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Experience Cloud ID {#experience-cloud-id}

The Adobe Experience Platform Identity Service provides a universal visitor ID across Experience Cloud solutions. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.

>[!TIP]
>
>You do not need to populate the Experience Cloud ID unless you are using the Adobe Experience Platform Identity Service. For more information, see [Adobe Experience Platform Identity Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**Requiere el SDK versión 4.3 o posterior**

## Habilitar el ID de Experience Cloud {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración al proyecto* en Implementación [principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Compruebe que los `ADBMobileConfig.json` archivos contengan la `marketingCloud` variable `org`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Los ID de organización de Experience Cloud permiten identificar de forma exclusiva cada empresa cliente en Adobe Experience Cloud y tienen un valor similar a este: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Debe incluir `@AdobeOrg`.

   If these values are not present, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Para obtener más información, consulte Configuración [JSON de ADBMobile](/help/ios/getting-started/requirements.md).

Tras completar la configuración, se genera un Experience Cloud ID que se incluye en todas las visitas. Otros ID de visitante, como los ID personalizados y los generados automáticamente, se siguen enviando con cada visita.
