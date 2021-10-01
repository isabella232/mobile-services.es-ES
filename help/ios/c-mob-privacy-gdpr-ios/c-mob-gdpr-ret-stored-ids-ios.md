---
description: Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.
title: Recuperación de identificadores almacenados
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 67%

---

# Recuperación de identificadores almacenados{#retrieving-stored-identifiers}

Esta información le ayuda a recuperar identidades del SDK de Experience Cloud almacenadas localmente desde su aplicación iOS con solicitudes de acceso a los datos del RGPD.

Para obtener más información sobre el RGPD, consulte [RGPD y su empresa](https://www.adobe.com/es/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>El método `getAllIdentifiersAsync` recupera las identidades almacenadas en los SDK de Experience Cloud. Debe llamar a este método **antes** de que el usuario se excluya.

Las identidades del SDK de Experience Cloud (según corresponda) se almacenan localmente y se devuelven en una cadena JSON, que puede contener:

* Contexto de compañía: ID de organización de IMS
* ID de usuario
* Experience Cloud ID (MID), antes denominado Experience Cloud ID
* Códigos de integración (ADID, Push ID)
* ID de fuentes de datos (DPID, DPUUID)
* ID de Analytics (AVID, AID, VID y RSID asociados)
* ID heredados de Target (TNTID, TNT3rdpartyID)
* ID de Audience Manager (UUID)

Aquí tiene un ejemplo del método `ADBMobile getAllIdentifiersAsync` en iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
