---
description: Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.
seo-description: Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.
seo-title: Recuperación de identificadores almacenados
title: Recuperación de identificadores almacenados
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 69%

---


# Recuperación de identificadores almacenados{#retrieving-stored-identifiers}

Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.

Para obtener más información sobre el RGPD, consulte [RGPD y su empresa](https://www.adobe.com/es/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>El método `getAllIdentifiersAsync` recupera las identidades almacenadas en los SDK de Experience Cloud. You must call this method **before** the user opts-out.

Las identidades del SDK de Experience Cloud (según corresponda) se almacenan localmente y se devuelven en una cadena JSON, que puede contener:

* Contexto de compañía: ID de organización de IMS
* ID de usuario
* Experience Cloud ID (MID), antes denominado Experience Cloud ID
* Códigos de integración (ADID, Push ID)
* ID de fuentes de datos (DPID, DPUUID)
* ID de Analytics (AVID, AID, VID y RSID asociados)
* ID de destinatario heredados (TNTID, TNT3rdpartyID)
* ID de Audience Manager (UUID)

Aquí tiene un ejemplo del método `ADBMobile getAllIdentifiersAsync` en iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

