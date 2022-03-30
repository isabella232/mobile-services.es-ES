---
description: El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
solution: Experience Cloud Services,Analytics
title: Experience Cloud ID
topic-fix: Developer and implementation
uuid: 13628ea8-3cd4-4cfc-8ff6-722c33f7813a
exl-id: aa7db365-ad21-431f-bff6-2a6da212dd0c
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 91%

---

# ID de Experience Cloud {#experience-cloud-id}

El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.

>[!TIP]
>
>No es necesario rellenar el Experience Cloud ID, salvo en el caso de que esté utilizando el servicio de ID de Adobe Experience Platform. Para obtener más información, consulte la [Servicio de identidad de Adobe Experience Platform](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=es) documentación.

## Habilitar el Experience Cloud ID {#section_79F984271C3B4366B7B04F864F4FF8C2}

Estos pasos requieren una versión 4.3 o posterior del SDK.

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
