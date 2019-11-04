---
description: A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.
seo-description: A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.
seo-title: 'Android Wearables: Notas adicionales'
solution: Experience Cloud,Analytics
title: 'Android Wearables: Notas adicionales'
topic: Desarrollador e implementación
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: Notas adicionales{#android-wearables-additional-notes}

A continuación encontrará información de ayuda para configurar la extensión de Android, lo cual le permitirá recopilar datos de su aplicación Android Wearable.

* La extensión Android Wearables de Adobe Mobile requiere la versión 4.4 (KitKat) o posterior de Android.
* Hay un valor de contexto adicional, `A.RunMode`, que se ha añadido para indicar si los datos proceden de la aplicación contenedora o de la extensión.

   * `RunMode` = `Application`

      La visita procede de la aplicación Handheld.

   * `RunMode` = `Extension`

      La visita procede de la aplicación Wearable.

* El SDK sincroniza automáticamente el estado de `aid`/`vid`/`visitor` `service id`/`privacy` de la aplicación Handheld en la aplicación Wearable, de modo que no llame a `setPrivacyStatus`/`setUserIdentifier`/`idSync`/ desde la aplicación Wearable.
* [Los mensajes en la aplicación](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) y [Audience Manager](/help/android/audience-manager/audiencemgmt.md) están desactivados para la aplicación Wearable.

