---
description: El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-description: El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-title: Experience Cloud ID
solution: Experience Cloud,Analytics
title: Experience Cloud ID
topic: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---


# Experience Cloud ID {#experience-cloud-id}

El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.

>[!TIP]
>
>No es necesario rellenar el Experience Cloud ID, salvo en el caso de que esté utilizando el servicio de ID de Adobe Experience Platform. Para obtener más información, consulte [Servicio de ID de Adobe Experience Platform](https://docs.adobe.com/content/help/es-ES/id-service/using/home.html).

**Requiere el SDK versión 4.3 o posterior**

## Habilitar el Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Compruebe que los archivos `ADBMobileConfig.json` contienen el `marketingCloud` `org`:

   ```js
   "marketingCloud" : { 
     "org": "YOUR-MCORG-ID" 
   }
   ```

   Los ID de organización de Experience Cloud permiten identificar de forma exclusiva cada empresa cliente en Adobe Experience Cloud y tienen un valor similar a este: `016D5C175213CCA80A490D05@AdobeOrg`.

   >[!IMPORTANT]
   >
   >Debe incluir `@AdobeOrg`.

   Si estos valores no están presentes, descargue un archivo `ADBMobileConfig.json` actualizado desde Adobe Mobile Services. Para obtener más información, consulte [Configuración JSON de ADBMobile](/help/ios/getting-started/requirements.md).

Después de la configuración, se genera un ID de Experience Cloud que se incluye en todas las visitas. Otros ID de visitante, como los ID personalizados y los generados automáticamente, se siguen enviando con cada visita.
