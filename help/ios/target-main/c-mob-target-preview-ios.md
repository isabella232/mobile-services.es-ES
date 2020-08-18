---
description: La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.
seo-description: La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.
seo-title: Vista previa de Target en iOS
title: Vista previa de Target en iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: ht
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: ht
source-wordcount: '141'
ht-degree: 100%

---


# Vista previa de Target en iOS {#target-preview-on-ios}

La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.

Para obtener más información acerca de cómo configurar y utilizar Vista previa de Target, consulte [Vista previa de Target Mobile](https://docs.adobe.com/content/help/es-ES/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Para utilizar Vista previa de Target, necesitará la versión 4.14.0 o posterior del SDK.

## Método de Vista previa de Target

* **setPreviewRestartDeeplink**

   Establece un vínculo profundo de la aplicación que se activará cuando se apliquen las selecciones de previsualización en el modo de Previsualización.

   * Esta es la sintaxis para este método:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
