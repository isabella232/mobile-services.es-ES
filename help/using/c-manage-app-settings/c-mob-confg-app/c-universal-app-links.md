---
description: Los vínculos universales (iOS) y los vínculos de aplicación (Android) le permiten conectarse a vínculos profundos en sus aplicaciones de iOS o Android.
keywords: móvil
seo-description: Los vínculos universales (iOS) y los vínculos de aplicación (Android) le permiten conectarse a vínculos profundos en sus aplicaciones de iOS o Android.
seo-title: Apple Universal Links y Android App Links
solution: Marketing Cloud,Analytics
title: Apple Universal Links y Android App Links
topic: Métricas
uuid: 8d6441dc-4307-4454-95ea-d77ec796f918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Apple Universal Links and Android App Links{#universal-links-and-app-links}

Universal Links (iOS) and App Links (Android) allow you to connect to deep links in your iOS or Android apps.

>[!IMPORTANT]
>
>A partir de iOS 9.2, no se admite la vinculación profunda. Debe utilizar los vínculos universales de Apple para la vinculación profunda a su aplicación o sitio web.

## Vínculos universales {#section_F8147944679A42E59CF4FD8814E5EF12}

Los vínculos universales le permiten conectarse a vínculos profundos en su aplicación de iOS y son compatibles con iOS 9.2 o posterior. Cuando se accede a un vínculo universal, iOS redirige el vínculo directamente al vínculo profundo de la aplicación. Si la aplicación no está instalada, se abre una URL para el sitio web en un navegador. Para obtener más información sobre los vínculos universales, consulte [Compatibilidad con vínculos](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html)universales.

## Vínculos de la aplicación

Los vínculos de aplicación le permiten conectarse a vínculos profundos en su aplicación de Android y se admiten en Android 6.0 o posterior. Cuando se accede a un vínculo de aplicación, Android redirige el vínculo directamente al vínculo profundo de la aplicación. Si la aplicación no está instalada, se abre una URL para el sitio web en un navegador. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Creación de un vínculo de marketing mediante un vínculo universal o de aplicación {#section_609ADEFFB9B441C4A8C45E936D0DC859}

You can create a Marketing Link that uses a Universal or App Link.

### Configurar un vínculo universal

1. Para configurar los vínculos universales en la aplicación de iOS, vaya a [Gestión de vínculos universales en Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. En Adobe Mobile Services, configure los documentos de asociación de sitios:

   a. En la página de inicio de Mobile Services, seleccione la aplicación para la que desea configurar los vínculos universales.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Asegúrese de que la aplicación de iOS que gestiona los vínculos universales se agrega a la sección **[!UICONTROL Agregar aplicaciones]** de App Store.

   >[!TIP]
   >
   >If the Add App Store Apps section does not display, click the Add App Store App link.********

   d. En la sección Opciones **[!UICONTROL de vínculos]** universales y de aplicación, seleccione una aplicación de iOS y escriba el ID de la aplicación.

   f.Haga clic en **[!UICONTROL Guardar]**.

   Debe seleccionar al menos una aplicación de iOS y un ID de aplicación, o bien recibirá un error.

   >[!IMPORTANT]
   >
   >Para actualizar los documentos, haga clic en la opción Actualizar de la sección Opciones de los vínculos universales y de la aplicación. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Uso de un vínculo universal

1. In Adobe Mobile Services, create a Marketing Link that uses Universal Links:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Click Create New.****

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. If you configured the site-association documents in the Setting up site-association documents in Adobe Mobile Services section above, this option is selected by default.**

   If you did not configure the documents, the Use Universal Links or App Links option is disabled and Use Interstitials is selected by default.********

   e. Si la opción **[!UICONTROL Usar vínculos universales o Vínculos]** de aplicación está seleccionada, se muestra el campo Ruta **** personalizada.

   Aquí los usuarios pueden definir la ruta de URL después del dominio, así como parámetros de consulta. Por ejemplo, si escribe , your full Marketing Link URL becomes .`my/universal/link?os=9.2``https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`

   f. Haga clic en la ficha **[!UICONTROL Decisiones]** y configure el árbol de decisiones.

   h. If the iOS app is installed, the app handles the deeplink with its logic. The final destination serves only as the fallback when the app is not installed. Since the app is not installed, the final destination can only be a web link or app store.

   i. Click Save.****

>[!TIP]
>
>Once a Marketing Link is saved, the Marketing Links Options cannot be altered. Esto se debe a que no desea cambiar el comportamiento de los vínculos de marketing que ya se han distribuido.


### Configure an App Link

1. To set up App Links in your Android app, go to [Add Android App Links](https://developer.android.com/studio/write/app-link-indexing).

1. En Adobe Mobile Services, configure los documentos de asociación de sitios:

   a. En la página de inicio de Mobile Services, seleccione la aplicación para la que desea configurar los vínculos de la aplicación.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Asegúrese de que la aplicación de Android que gestiona los vínculos universales o los vínculos de la aplicación se agrega a la sección **[!UICONTROL Agregar aplicaciones]** de App Store.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Desplácese a la sección Opciones **[!UICONTROL de vínculos]** universales y de aplicación.

   e. Haga clic en la ficha Vínculos **[!UICONTROL de aplicación (Android)]** .

   f. Seleccione una aplicación de Android y escriba una huella de certificado SHA-256.

   g.Haga clic en **[!UICONTROL Guardar]**.

   You must provide at least one Android app selection and one SHA-256 certificate, or you will receive an error.

   >[!IMPORTANT]
   >
   >Para actualizar los documentos, haga clic en la opción **[!UICONTROL Actualizar]** de la sección **Opciones de los vínculos universales y de la aplicación[!UICONTROL .]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Uso de un vínculo de aplicación

1. En Adobe Mobile Services, cree un vínculo de marketing que utilice vínculos de aplicación:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Haga clic en **[!UICONTROL Crear nuevo]**.

   c. En la sección Opciones **[!UICONTROL de vínculo]** de marketing, seleccione **[!UICONTROL Utilizar vínculos universales o vínculos]** de aplicación.

   d. Si ha configurado los documentos de asociación de sitios del paso 2, esta opción está seleccionada de forma predeterminada.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. If Use Universal Links or App Links is selected, the Custom Path field is displayed.********

   Aquí los usuarios pueden definir la ruta de URL después del dominio, así como parámetros de consulta. Por ejemplo, si escribe `my/app/link?os=6.0`, la dirección URL completa del vínculo de marketing se convierte en `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Haga clic en la ficha **[!UICONTROL Decisiones]** y configure el árbol de decisiones.

   g. If the Android app is installed, the app handles the deeplink with its logic.

   El destino final solo sirve como alternativa cuando la aplicación no está instalada. Como la aplicación no está instalada, el destino final solo puede ser un vínculo web o una tienda de aplicaciones.

   h.Haga clic en **[!UICONTROL Guardar]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. Esto se debe a que no desea cambiar el comportamiento de los vínculos de marketing que ya se han distribuido.

## Uso de vínculos de marketing

Ahora puede utilizar estos vínculos de marketing en mensajes y otras áreas de la aplicación.

>[!IMPORTANT]
>
>No verá recuentos de rastreo de clics con vínculos universales o vínculos de aplicación, y tampoco podrá utilizar intersticiales.

