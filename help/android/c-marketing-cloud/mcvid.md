---
description: El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-description: El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.
seo-title: Configuración de Experience Cloud ID
solution: Marketing Cloud,Analytics
title: Configuración de Experience Cloud ID
topic: Developer and implementation
uuid: 8ebdf2bf-c581-448f-9542-f99a19784fe7
translation-type: ht
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---


# Configuración de Experience Cloud ID {#experience-cloud-id-configuration}

El servicio de ID de ID de Adobe Experience Platform proporciona un ID de visitante universal para las distintas soluciones de Experience Cloud. Analytics requiere el servicio de ID para Target, Video Heartbeat y futuras integraciones de Experience Cloud.

>[!TIP]
>
>No es necesario rellenar el ID, salvo en el caso de que esté utilizando el servicio de ID de Adobe Experience Platform. Para obtener más información, consulte [Servicio de ID de Adobe Experience Platform](https://docs.adobe.com/content/help/es-ES/id-service/using/home.html).

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

Una vez completada la configuración, se genera un ID de Experience Cloud que se incluye en todas las visitas. Otros ID, como los personalizados y los generados automáticamente, se siguen enviando con cada visita.
