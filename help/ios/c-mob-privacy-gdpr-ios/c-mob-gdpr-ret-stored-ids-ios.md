---
description: Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.
seo-description: Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.
seo-title: Recuperación de identificadores almacenados
title: Recuperación de identificadores almacenados
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Recuperación de identificadores almacenados{#retrieving-stored-identifiers}

Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.

Para obtener más información sobre el RGPD, consulte [RGPD y tu negocio](https://www.adobe.com/es/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>El método `getAllIdentifiersAsync` recupera las identidades almacenadas en los SDK de Experience Cloud. Debe llamar este método **antes** de que el usuario cancele la solicitud.

Las identidades del SDK de Experience Cloud (según corresponda) se almacenan localmente y se devuelven en un archivo JSON, que puede contener:

* Contexto sobre la empresa: ID de organización de IMS
* ID de usuarios
* Experience Cloud ID (MID), antes denominado Experience Cloud ID
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

