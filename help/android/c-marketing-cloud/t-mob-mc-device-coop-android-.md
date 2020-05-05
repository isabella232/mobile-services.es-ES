---
description: Para inicio con la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.
seo-description: Para inicio con la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.
seo-title: Cooperación entre dispositivos de Experience Cloud
title: Cooperación entre dispositivos de Experience Cloud
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Cooperación entre dispositivos de Experience Cloud {#experience-cloud-device-co-op}

Para inicio con la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.

Para habilitar sus aplicaciones móviles para la cooperación entre dispositivos de Experience Cloud, complete los siguientes pasos para los SDK para Android de Experience Cloud:

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.8.3 o posterior del SDK para Android.

A partir de la versión 4.16.1 del SDK, los miembros de Device Co-op pueden desactivar los datos de sus dispositivos móviles en Experience Cloud Device Co-op. Para obtener más información, consulte [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) y el `visitorAPI.js` método [isCoopSafe](https://docs.adobe.com/content/help/en/id-service/using/id-service-api/configurations/coopsafe.html).

1. Implemente el SDK de Adobe Mobile.

   Para obtener más información, consulte [Implementación principal y ciclo vital](/help/android/getting-started/dev-qs.md).
1. Habilite su Experience Cloud ID.

   Para obtener más información, consulte [Configuración de Experience Cloud ID](/help/android/c-marketing-cloud/mcvid.md).
1. Transfiera los identificadores autenticados, como los de CRM o correos electrónicos con hash, utilizando uno de los métodos de sincronización.

   Para obtener más información, consulte [Servicio de ID de Adobe Experience Platform](/help/android/c-marketing-cloud/mc-methods.md).

## Indicador `coopUnsafe`

Aquí puede encontrar más información sobre el marcador `coopUnsafe`:

* Versión mínima del SDK: 4.16.1
* La propiedad booleana del objeto de `marketingCloud` que, cuando se establece en `true`, hará que el dispositivo sea excluido de la Device Co-Op de Experience Cloud.
* El valor predeterminado es `false`.
* Este ajuste **solo** se utiliza para clientes proporcionados por Device Co-op.

Para los miembros de Device Co-op que necesitan que este valor se establezca en `true`, necesitará colaborar con el equipo de Co-op para solicitar un marcador de lista negra en su cuenta de Device Co-op. No existe una ruta de autoservicio que permita habilitar estos indicadores.

Recuerde la información siguiente:

* Cuando `coopUnsafe` está establecido en `true`, `coop_unsafe=1` se añadirá siempre a las coincidencias de Audience Manager y Visitor ID.
* Si activa el reenvío del lado del servidor de Analytics a Audience Manager, también verá `coop_unsafe=1` en las coincidencias de Analytics.