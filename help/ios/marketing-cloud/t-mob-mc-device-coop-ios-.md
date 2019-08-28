---
description: Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.
seo-description: Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.
seo-title: Cooperación entre dispositivos de Experience Cloud
title: Cooperación entre dispositivos de Experience Cloud
uuid: 434 a 6 f 8 f-ec 24-439 d -95 f 0-a 246 b 384 b 3 b 5
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Cooperación entre dispositivos de Experience Cloud {#experience-cloud-device-co-op}

Para empezar a utilizar la cooperación entre dispositivos de Experience Cloud, póngase en contacto con su representante de Adobe.

Si quiere habilitar sus aplicaciones móviles para la cooperación entre dispositivos de Experience Cloud, complete los siguientes pasos para los SDK para iOS de Experience Cloud:

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.8.5 o posterior del SDK para iOS.

Empezando en la versión 4.16.1 de SDK, los miembros de Device Co-op pueden excluir sus datos de dispositivo móvil del Device Co-op de Experience Cloud. Para obtener más información, consulte [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md) y el método `visitorAPI.js` para [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html).

1. Implemente el SDK de Adobe Mobile.

   Para obtener más información, consulte [Implementación principal y Ciclo vital](/help/ios/getting-started/dev-qs.md).
1. Habilite su Experience Cloud ID.

   For more information, see [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. Pase identidades autenticadas, como ID de CRM o correos electrónicos con hash, utilizando uno de los métodos de sincronización contenidos aquí.

   Para obtener más información, consulte [Métodos de servicio de identidad de Adobe Experience Platform](/help/ios/marketing-cloud/mc-methods.md).

## `coopUnsafe` indicador

Here is some additional information on the `coopUnsafe` flag:

* Versión mínima del SDK: 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* El valor predeterminado es `false`.
* Este ajuste **solo** se utiliza para clientes proporcionados por Device Co-op.

Para los miembros de Device Co-op que necesitan que este valor se establezca en `true`, necesitará colaborar con el equipo de Co-op para solicitar un marcador de lista negra en su cuenta de Device Co-op. No existe una ruta de autoservicio que permita habilitar estos indicadores.

Recuerde la información siguiente:

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* Si activa el reenvío del lado del servidor de Analytics a Audience Manager, también verá `coop_unsafe=1` en las coincidencias de Analytics.


