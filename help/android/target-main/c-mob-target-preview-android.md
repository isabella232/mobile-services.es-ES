---
description: La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.
seo-description: La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.
seo-title: Vista previa de Target en Android
title: Vista previa de Target en Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 87%

---


# Vista previa de Target en Android {#target-preview-on-android}

La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://docs.adobe.com/content/help/es-ES/target/using/implement-target/mobile-apps/target-mobile-preview.html).

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
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

