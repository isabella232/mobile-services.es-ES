---
description: El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-description: El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-title: Configuración de Experience Cloud ID
solution: Experience Cloud,Analytics
title: Configuración de Experience Cloud ID
topic: Desarrollador e implementación
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Configuración de Experience Cloud ID {#experience-cloud-id-configuration}

El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.

>[!TIP]
>
>No es necesario rellenar el ID, salvo en el caso de que esté utilizando el servicio de ID de Adobe Experience Platform. Para obtener más información, consulte [Servicio de ID de Adobe Experience Platform](https://marketing.adobe.com/resources/help/es_ES/mcvid/).

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.3 o posterior del SDK.

Para habilitar el Experience Cloud ID:

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Compruebe que los archivos `ADBMobileConfig.json` contienen el `marketingCloudorg`:

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
   >Debe incluir `@AdobeOrg`.

   Si estos ID no están configurados, descargue un archivo `ADBMobileConfig.json` actualizado desde Adobe Mobile Services. Para obtener más información, consulte [Antes de comenzar](/help/android/getting-started/requirements.md).

Tras completar la configuración, se genera un Experience Cloud ID que se incluye en todas las visitas. Otros ID, como los ID personalizados y los generados automáticamente, se siguen enviando con cada visita.
