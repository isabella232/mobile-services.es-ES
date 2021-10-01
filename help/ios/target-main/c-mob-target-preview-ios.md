---
description: La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.
title: Vista previa de Target en iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 76%

---

# Vista previa de Target en iOS{#target-preview-on-ios}

La vista previa de Target permite realizar un completo QA para actividades de Target y previsualizar estas actividades en el dispositivo.

Para obtener más información sobre cómo configurar y utilizar Vista previa de Target, consulte [Vista previa para móviles de Target](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) en la documentación de Adobe Target.

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
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```
