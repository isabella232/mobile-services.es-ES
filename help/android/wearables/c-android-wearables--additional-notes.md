---
description: A continuación se proporciona información para ayudarle a configurar la extensión de Android, que le permite recopilar datos de su aplicación Android Wearable.
seo-description: A continuación se proporciona información para ayudarle a configurar la extensión de Android, que le permite recopilar datos de su aplicación Android Wearable.
seo-title: 'Android Wearables: Notas adicionales'
solution: Experience Cloud,Analytics
title: 'Android Wearables: Notas adicionales'
topic: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 51%

---


# Android Wearables: Notas adicionales{#android-wearables-additional-notes}

A continuación se proporciona información para ayudarle a configurar la extensión de Android, que le permite recopilar datos de su aplicación Android Wearable.

* La extensión Android Wearables para móviles Adobe requiere Android versión 4.4 (KitKat) o superior.
* Hay un valor de contexto adicional, `A.RunMode`, que se ha añadido para indicar si los datos proceden de la aplicación contenedora o de la extensión.

   * `RunMode` = `Application`

      La visita procede de la aplicación Handheld.

   * `RunMode` = `Extension`

      La visita procede de la aplicación Wearable.

* El SDK sincroniza automáticamente el estado de `aid`/`vid`/`visitor` `service id`/`privacy` de la aplicación Handheld en la aplicación Wearable, de modo que no llame a `setPrivacyStatus`/`setUserIdentifier`/`idSync`/ desde la aplicación Wearable.
* [Los mensajes en la aplicación](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) y [Audience Manager](/help/android/audience-manager/audiencemgmt.md) están desactivados para la aplicación Wearable.

