---
description: La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.
title: Vista previa de Target en Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 74%

---

# Vista previa de Target en Android {#target-preview-on-android}

La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.

Para obtener más información sobre cómo configurar y utilizar Vista previa de Target, vaya a [Vista previa de Target Mobile](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) en la guía del usuario de Adobe Target.

>[!IMPORTANT]
>
>Para utilizar Vista previa de Target, necesitará la versión 4.14.0 o posterior del SDK.

* **setPreviewRestartDeeplink**

   Establece un vínculo profundo de la aplicación que se activará cuando se apliquen las selecciones de previsualización en el modo de Previsualización.

   * Esta es la sintaxis para este método:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Target.setPreviewRestartDeeplink("myapp://myhost"); 
      ```
