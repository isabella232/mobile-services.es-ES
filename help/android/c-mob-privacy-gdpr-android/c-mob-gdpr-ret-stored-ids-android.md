---
description: Esta información le permite recuperar identidades del SDK almacenados de forma local de su aplicación Android y con solicitudes de acceso a datos RGPD.
seo-description: Esta información le permite recuperar identidades del SDK almacenados de forma local de su aplicación Android y con solicitudes de acceso a datos RGPD.
seo-title: Recuperación de identificadores almacenados
title: Recuperación de identificadores almacenados
uuid: 6 fd 3 d 202-b 0 a 1-4 c 80-96 f 4-369 fc 24 ac 0 a 3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Esta información le permite recuperar identidades del SDK almacenados de forma local de su aplicación Android y con solicitudes de acceso a datos RGPD.

>[!IMPORTANT]
>
>`getAllIdentifiersAsync` El método recupera identidades almacenadas en el SDK. Debe llamar este método **antes** de que el usuario opte por la exclusión.

Las identidades del SDK (según se aplique) se almacenan de forma local y se devuelven en una cadena JSON, que puede contener:

* Contexto de la empresa: ID de organización IMS
* ID de usuarios
* Experience Cloud ID (MID), antes denominado Marketing Cloud ID
* Códigos de integración (ADID, Push ID)
* ID de orígenes de datos (DPID, DPUUID)
* ID de Analytics (AVID, AID, VID y RSID asociados)
* ID de legado de Target (TNTID, TNT3rdpartyID)
* ID de Audience Manager (UUID)

Este es un ejemplo del método `ADBMobile getAllIdentifiersAsync` en Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
