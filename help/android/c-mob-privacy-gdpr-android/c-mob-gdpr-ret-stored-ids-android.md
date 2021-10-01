---
description: Esta información le permite recuperar identidades del SDK almacenados de forma local de su aplicación Android y con solicitudes de acceso a datos RGPD.
title: Recuperación de identificadores almacenados
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 72%

---

# Recuperación de identificadores almacenados{#retrieving-stored-identifiers}

Esta información le permite recuperar identidades del SDK almacenados de forma local de su aplicación Android y con solicitudes de acceso a datos RGPD.

>[!IMPORTANT]
>
>El método `getAllIdentifiersAsync` recupera identidades almacenadas en el SDK. Debe llamar a este método **antes** de que el usuario se excluya.

Las identidades del SDK (según corresponda) se almacenan localmente y se devuelven en una cadena JSON, que puede contener:

* Contexto de compañía: ID de organización de IMS
* ID de usuario
* Experience Cloud ID (MID), antes denominado Experience Cloud ID
* Códigos de integración (ADID, Push ID)
* ID de fuentes de datos (DPID, DPUUID)
* ID de Analytics (AVID, AID, VID y RSID asociados)
* ID heredados de Target (TNTID, TNT3rdpartyID)
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
