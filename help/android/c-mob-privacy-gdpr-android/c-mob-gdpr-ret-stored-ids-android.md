---
description: Esta información le permite recuperar identidades del SDK almacenados de forma local de su aplicación Android y con solicitudes de acceso a datos RGPD.
seo-description: Esta información le permite recuperar identidades del SDK almacenados de forma local de su aplicación Android y con solicitudes de acceso a datos RGPD.
seo-title: Recuperación de identificadores almacenados
title: Recuperación de identificadores almacenados
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 76%

---


# Recuperación de identificadores almacenados{#retrieving-stored-identifiers}

Esta información le permite recuperar identidades del SDK almacenados de forma local de su aplicación Android y con solicitudes de acceso a datos RGPD.

>[!IMPORTANT]
>
>El método `getAllIdentifiersAsync` recupera identidades almacenadas en el SDK. You must call this method **before** the user opts-out.

Las identidades del SDK (según corresponda) se almacenan localmente y se devuelven en una cadena JSON, que puede contener:

* Contexto de compañía: ID de organización de IMS
* ID de usuario
* Experience Cloud ID (MID), antes denominado Experience Cloud ID
* Códigos de integración (ADID, Push ID)
* ID de fuentes de datos (DPID, DPUUID)
* ID de Analytics (AVID, AID, VID y RSID asociados)
* ID de destinatario heredados (TNTID, TNT3rdpartyID)
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
