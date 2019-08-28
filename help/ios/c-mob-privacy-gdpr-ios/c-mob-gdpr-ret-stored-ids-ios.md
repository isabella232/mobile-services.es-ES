---
description: Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.
seo-description: Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.
seo-title: Recuperación de identificadores almacenados
title: Recuperación de identificadores almacenados
uuid: 4 fb 2 c 166-6700-4 f 8 b-b 60 b -137 b 199 e 0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.

Para obtener más información sobre el RGPD, consulte [RGPD y tu negocio](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` El método recupera identidades almacenadas en los SDK de Experience Cloud. Debe llamar este método **antes** de que el usuario cancele la solicitud.

Las identidades del SDK de Experience Cloud (según corresponda) se almacenan localmente y se devuelven en un archivo JSON, que puede contener:

* Contexto sobre la empresa: ID de organización de IMS
* ID de usuarios
* Experience Cloud ID (MID), antes denominado Marketing Cloud ID
* Códigos de integración (ADID, Push ID)
* ID de orígenes de datos (DPID, DPUUID)
* ID de Analytics (AVID, AID, VID y RSID asociados)
* ID de legado de Target (TNTID, TNT3rdpartyID)
* ID de Audience Manager (UUID)

Aquí tiene un ejemplo del método `ADBMobile getAllIdentifiersAsync` en iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

