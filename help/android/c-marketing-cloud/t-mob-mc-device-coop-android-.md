---
description: Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.
seo-description: Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.
seo-title: Cooperación entre dispositivos de Experience Cloud
title: Cooperación entre dispositivos de Experience Cloud
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: ht
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Cooperación entre dispositivos de Experience Cloud {#experience-cloud-device-co-op}

Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.

Si quiere habilitar sus aplicaciones móviles para la cooperación entre dispositivos de Experience Cloud, complete los siguientes pasos para los SDK para Android de Experience Cloud:

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.8.3 o posterior del SDK para Android.

Empezando en la versión 4.16.1 de SDK, los miembros de Device Co-op pueden excluir sus datos de dispositivo móvil del Device Co-op de Experience Cloud. Para obtener más información, consulte [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) y el método `visitorAPI.js` para [isCoopSafe](https://docs.adobe.com/content/help/pt-BR/mobile-services/ios/rel-notes.html).

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