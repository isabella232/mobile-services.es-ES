---
description: A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.
seo-description: A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.
seo-title: Notas adicionales de Android Wearables
solution: Marketing Cloud,Analytics
title: Notas adicionales de Android Wearables
topic: Desarrollador e implementación
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.

* La extensión Android Wearables de Adobe Mobile requiere la versión 4.4 (KitKat) o posterior de Android.
* Hay un valor de contexto adicional, `A.RunMode`, que se ha añadido para indicar si los datos proceden de la aplicación contenedora o de la extensión.

   * `RunMode` = `Application`

      The hit comes from the handheld app.

   * `RunMode` = `Extension`

      The hit comes from the wearable app.

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [In-app messages, Target, and Audience Manager are disabled for the wearable app.](/help/android/messaging-main/messaging/messaging.md)[](/help/android/target-main/target.md)[](/help/android/audience-manager/audiencemgmt.md)

