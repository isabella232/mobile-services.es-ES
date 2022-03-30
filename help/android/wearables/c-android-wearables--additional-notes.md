---
description: A continuación se proporciona información para ayudarle a configurar la extensión de Android que le permite recopilar datos de su aplicación Android Wearable.
solution: Experience Cloud Services,Analytics
title: 'Android Wearables: Notas adicionales'
topic-fix: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
exl-id: ae8cf2d1-d2b0-456b-bbd3-3980e00bbc84
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 100%

---

# Android Wearables: Notas adicionales {#android-wearables-additional-notes}

A continuación se proporciona información para ayudarle a configurar la extensión de Android que le permite recopilar datos de su aplicación Android Wearable.

* La extensión Adobe Mobile Android Wearables requiere Android versión 4.4 (KitKat) o superior.
* Hay un valor de contexto adicional, `A.RunMode`, que se ha añadido para indicar si los datos proceden de la aplicación contenedora o de la extensión.

   * `RunMode` = `Application`

      La visita procede de la aplicación Handheld.

   * `RunMode` = `Extension`

      La visita procede de la aplicación Wearable.

* El SDK sincroniza automáticamente el estado de `aid`/`vid`/`visitor` `service id`/`privacy` de la aplicación Handheld en la aplicación Wearable, de modo que no llame a `setPrivacyStatus`/`setUserIdentifier`/`idSync`/ desde la aplicación Wearable.
* [Los mensajes en la aplicación](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) y [Audience Manager](/help/android/audience-manager/audiencemgmt.md) están desactivados para la aplicación Wearable.
