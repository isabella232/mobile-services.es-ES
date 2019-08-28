---
description: La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.
seo-description: La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.
seo-title: Vista previa de Target en iOS
title: Vista previa de Target en iOS
uuid: d 92867 a 4-0569-4732-a 928-28 f 9 e 2 f 8 b 21 e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Vista previa de Target en iOS{#target-preview-on-ios}

La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.

For more information on how to set up and use Target Preview, see [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Para usar la Vista previa de Target necesita la versión 4.14.0 o posterior del SDK.

## Método de vista previa de objetivo

* **setPreviewRestartDeeplink**

   Establece un enlace profundo de aplicación que se activará cuando las selecciones de vista de previa se apliquen en el modo Vista previa.

   * Esta es la sintaxis para este método:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
