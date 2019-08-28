---
description: Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.
seo-description: Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.
seo-title: Cooperación entre dispositivos de Experience Cloud
title: Cooperación entre dispositivos de Experience Cloud
uuid: 7 bb 8 a 19 c -4 b 80-4911-879 d-f 9941 baa 3 b 62
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Cooperación entre dispositivos de Experience Cloud {#experience-cloud-device-co-op}

Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.

Si quiere habilitar sus aplicaciones móviles para la cooperación entre dispositivos de Experience Cloud, complete los siguientes pasos para los SDK para Android de Experience Cloud:

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.8.3 o posterior del SDK para Android.

Empezando en la versión 4.16.1 de SDK, los miembros de Device Co-op pueden excluir sus datos de dispositivo móvil del Device Co-op de Experience Cloud. Para obtener más información, consulte [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) y el método `visitorAPI.js` para [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html).

1. Implemente el SDK de Adobe Mobile.

   Para obtener más información, consulte [Implementación principal y Ciclo vital](/help/android/getting-started/dev-qs.md).
1. Habilite su Experience Cloud ID.

   For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).
1. Transfiera los identificadores autenticados, como los de CRM o correos electrónicos con hash, utilizando uno de los métodos de sincronización.

   Para obtener más información, consulte [Métodos de servicio de identidad de Adobe Experience Platform](/help/android/c-marketing-cloud/mc-methods.md).

## `coopUnsafe` indicador

Aquí puede encontrar más información sobre el marcador `coopUnsafe`:

* Versión mínima del SDK: 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* El valor predeterminado es `false`.
* Este ajuste **solo** se utiliza para clientes proporcionados por Device Co-op.

Para los miembros de Device Co-op que necesitan que este valor se establezca en `true`, necesitará colaborar con el equipo de Co-op para solicitar un marcador de lista negra en su cuenta de Device Co-op. No existe una ruta de autoservicio que permita habilitar estos indicadores.

Recuerde la información siguiente:

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.