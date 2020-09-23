---
description: Los vínculos universales (iOS) y los vínculos de aplicación (Android) le permiten conectarse a vínculos profundos en sus aplicaciones de iOS o Android.
keywords: mobile
seo-description: Los vínculos universales (iOS) y los vínculos de aplicación (Android) le permiten conectarse a vínculos profundos en sus aplicaciones de iOS o Android.
seo-title: Vínculos universales de Apple y de la aplicación de Android
solution: Experience Cloud,Analytics
title: Vínculos universales de Apple y de la aplicación de Android
topic: Metrics
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 97%

---


# Vínculos universales de Apple y de la aplicación de Android{#universal-links-and-app-links}

Los vínculos universales (iOS) y los vínculos de aplicación (Android) le permiten conectarse a vínculos profundos en sus aplicaciones de iOS o Android.

>[!IMPORTANT]
>
>A partir de iOS 9.2, la vinculación profunda no es compatible. Debe utilizar los vínculos universales de Apple para la vinculación profunda a su aplicación o sitio web.

## Vínculos universales {#section_F8147944679A42E59CF4FD8814E5EF12}

Los vínculos universales le permiten conectarse a vínculos profundos en su aplicación de iOS y son compatibles con iOS 9.2 y posteriores. Cuando se accede a un vínculo universal, iOS lo redirige directamente al vínculo profundo de la aplicación. Si la aplicación no está instalada, se abre una URL para el sitio web en un navegador. Para obtener más información sobre los vínculos universales, consulte [Compatibilidad con vínculos universales](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Vínculos de la aplicación

Los vínculos de aplicación le permiten conectarse a vínculos profundos en su aplicación de Android y son compatibles en Android 6.0 y posteriores. Cuando se accede a un vínculo de aplicación, Android lo redirige directamente al vínculo profundo de la aplicación. Si la aplicación no está instalada, se abre una URL para el sitio web en un navegador. Para obtener más información sobre los vínculos de la aplicación, consulte [Gestión de vínculos de la aplicación de Android](https://developer.android.com/training/app-links/index.html).

## Creación de un vínculo de marketing mediante un vínculo universal o de aplicación {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Puede crear un vínculo de marketing que utilice un vínculo universal o de aplicación.

### Configurar un vínculo universal

1. Para configurar los vínculos universales en la aplicación de iOS, vaya a [Gestión de vínculos universales en Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. En Adobe Mobile Services, configure los documentos de asociación de sitios:

   En la página de inicio de Mobile Services, seleccione la aplicación en la que desea configurar vínculos universales.

   b. Haga clic en **[!UICONTROL Administrar configuración de aplicación]**.

   c. Compruebe que la aplicación de iOS que gestiona los vínculos universales se agrega a la sección **[!UICONTROL Agregar aplicaciones de App Store]**.

   >[!TIP]
   >
   >Si la sección **[!UICONTROL Agregar aplicaciones de tiendas de aplicaciones]** no se muestra, haga clic en el vínculo **[!UICONTROL Agregar aplicación de la tienda de aplicaciones]**.

   d. En la sección **[!UICONTROL Opciones de vínculos universales y de la aplicación]**, seleccione una aplicación de iOS y escriba el ID de la aplicación.

   f. Haga clic en **[!UICONTROL Guardar]**.

   Debe proporcional al menos una selección de aplicaciones de iOS y un ID de aplicación, de lo contrario obtendrá un error.

   >[!IMPORTANT]
   >
   >Para actualizar los documentos, haga clic en la opción Actualizar de la sección Opciones de los vínculos universales y de la aplicación. No obstante, al hacer clic en **[!UICONTROL Actualizar]**, una advertencia le avisa de que todos los vínculos universales y de aplicación que haya creado anteriormente se verán afectados.

### Use un vínculo universal

1. En Adobe Mobile Services, cree un vínculo de marketing que utilice vínculos universales:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. Haga clic en **[!UICONTROL Crear nuevo]**.

   c. En **[!UICONTROL Opciones del vínculo de marketing]**, seleccione **[!UICONTROL Usar los vínculos universales o los de la aplicación]**.

   d. Si ha configurado los documentos de asociación de sitios en la sección *Configuración de documentos de asociación de sitios en Adobe Mobile Services* que se encuentra arriba, esta opción estará seleccionada de forma predeterminada.

   Si no ha configurado los documentos, la opción **[!UICONTROL Usar los vínculos universales o los vínculos de la aplicación]** estará desactivada y la opción **[!UICONTROL Usar intersticiales]** estará activada de forma predeterminada.

   e. Si la opción **[!UICONTROL Utilizar vínculos universales o de aplicación]** está seleccionada, se muestra el campo **[!UICONTROL Ruta personalizada]**.

   Aquí los usuarios pueden definir la ruta de URL después del dominio, así como parámetros de consulta. Por ejemplo, si escribe `my/universal/link?os=9.2`, la dirección URL completa del vínculo de marketing se convierte en `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Haga clic en la pestaña **[!UICONTROL Decisiones]** y configure el árbol de decisiones.

   h. Si la aplicación de iOS está instalada, la aplicación gestiona el vínculo profundo con su lógica. El destino final solo sirve como alternativa cuando la aplicación no está instalada. Como la aplicación no está instalada, el destino final solo puede ser un vínculo web o una tienda de aplicaciones.

   i. Haga clic en **[!UICONTROL Guardar]**.

>[!TIP]
>
>Cuando se guarda un vínculo de marketing, las Opciones del vínculo de marketing no se pueden modificar. Esto se hace para que el comportamiento de los vínculos de marketing que se hayan podido distribuir no cambie.


### Configurar un vínculo de la aplicación

1. Para configurar los vínculos de la aplicación en la de Android, vaya a [Agregar vínculos de la aplicación de Android](https://developer.android.com/studio/write/app-link-indexing).

1. En Adobe Mobile Services, configure los documentos de asociación de sitios:

   a. En la página de inicio de Mobile Services, seleccione la aplicación en la que desea configurar vínculos de la aplicación.

   b. Haga clic en **[!UICONTROL Administrar configuración de aplicación]**.

   c. Compruebe que la aplicación de Android que gestiona los vínculos universales o los de la aplicación se agrega a la sección **[!UICONTROL Agregar aplicaciones de App Store]**.

   >[!TIP]
   >
   >Si esta sección no está visible, haga clic en el vínculo **[!UICONTROL Agregar aplicación de la tienda de aplicaciones]**.

   d. Desplácese a la sección **[!UICONTROL Opciones de vínculos universales y de aplicación]**.

   e. Haga clic en la ficha **[!UICONTROL Vínculos de la aplicación (Android)]**.

   f. Seleccione una aplicación de Android y escriba una huella de certificado SHA-256.

   g. Haga clic en **[!UICONTROL Guardar]**.

   Debe proporcional al menos una selección de aplicaciones de Android y un certificado SHA-256, de lo contrario obtendrá un error.

   >[!IMPORTANT]
   >
   >Para actualizar los documentos, haga clic en la opción **[!UICONTROL Actualizar]** de la sección **[!UICONTROL Opciones de los vínculos universales y de la aplicación]**. No obstante, al hacer clic en **[!UICONTROL Actualizar]**, una advertencia le avisa de que todos los vínculos universales y de aplicación que haya creado anteriormente se verán afectados.

### Uso de un vínculo de aplicación

1. En Adobe Mobile Services, cree un vínculo de marketing que utilice vínculos de aplicación:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** > **[!UICONTROL Marketing Link Builder]**.

   b. Haga clic en **[!UICONTROL Crear nuevo]**.

   c. En la sección **[!UICONTROL Opciones de vínculo de marketing,]** seleccione **[!UICONTROL Utilizar vínculos universales o de aplicación]**.

   d. Si configuró los documentos de asociación de sitios siguiendo el paso 2, esta opción está seleccionada de forma predeterminada.

   En caso contrario, la opción **[!UICONTROL Usar los vínculos universales o los vínculos de la aplicación]** estará desactivada y la opción **[!UICONTROL Usar intersticiales]** estará activada de forma predeterminada.

   e. Si **[!UICONTROL Utilizar vínculos universales o de aplicación]** está seleccionado, se muestra el campo **[!UICONTROL Ruta personalizada]**.

   Aquí los usuarios pueden definir la ruta de URL después del dominio, así como parámetros de consulta. Por ejemplo, si escribe `my/app/link?os=6.0`, la dirección URL completa del vínculo de marketing se convierte en `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Haga clic en la pestaña **[!UICONTROL Decisiones]** y configure el árbol de decisiones.

   g. Si la aplicación de Android está instalada, esta gestiona el vínculo profundo con su lógica.

   El destino final solo sirve como alternativa cuando la aplicación no está instalada. Como la aplicación no está instalada, el destino final solo puede ser un vínculo web o una tienda de aplicaciones.

   h.  Haga clic en **[!UICONTROL Guardar]**.

>[!TIP]
>
>Tras guardar un vínculo de marketing, las **[!UICONTROL Opciones del vínculo de marketing]** no se pueden modificar. Esto se hace para que el comportamiento de los vínculos de marketing que se hayan podido distribuir no cambie.

## Uso de vínculos de marketing

Ahora puede utilizar estos vínculos de marketing en mensajes y otras áreas de la aplicación.

>[!IMPORTANT]
>
>No verá recuentos de rastreo de clics con vínculos universales o de aplicación, y tampoco podrá utilizar intersticiales.

