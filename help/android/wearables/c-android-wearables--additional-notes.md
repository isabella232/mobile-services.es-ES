---
description: A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.
seo-description: A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.
seo-title: Notas adicionales de Android Wearables
solution: Marketing Cloud, Analytics
title: Notas adicionales de Android Wearables
topic: Desarrollador e implementación
uuid: 3 bcf 352 b -4 d 46-4 ab 3-81 ec-c 27 e 86 fe 9 be 3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.

* La extensión Android Wearables de Adobe Mobile requiere la versión 4.4 (KitKat) o posterior de Android.
* Hay un valor de contexto adicional, `A.RunMode`, que se ha añadido para indicar si los datos proceden de la aplicación contenedora o de la extensión.

   * `RunMode` = `Application`

      La visita procede de la aplicación de mano.

   * `RunMode` = `Extension`

      La visita procede de la aplicación Wearable.

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [Los mensajes en la aplicación](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md)y [Audience Manager](/help/android/audience-manager/audiencemgmt.md) están desactivados para la aplicación Wearable.

