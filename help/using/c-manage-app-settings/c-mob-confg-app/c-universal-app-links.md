---
description: Los vínculos universales (iOS) y los vínculos de aplicación (Android) le permiten conectarse a vínculos profundos en sus aplicaciones iOS o Android.
keywords: móvil
seo-description: Los vínculos universales (iOS) y los vínculos de aplicación (Android) le permiten conectarse a vínculos profundos en sus aplicaciones iOS o Android.
seo-title: Vínculos universales Apple y vínculos de aplicaciones Android
solution: Marketing Cloud, Analytics
title: Vínculos universales Apple y vínculos de aplicaciones Android
topic: Métricas
uuid: 8 d 6441 dc -4307-4454-95 ea-d 77 ec 796 f 918
translation-type: tm+mt
source-git-commit: e65add089499f728827321e96e439f04ebb19a73

---


# Vínculos universales Apple y vínculos de aplicaciones Android{#universal-links-and-app-links}

Los vínculos universales (iOS) y los vínculos de aplicación (Android) le permiten conectarse a vínculos profundos en sus aplicaciones iOS o Android.

>[!IMPORTANT]
>
>A partir de iOS 9.2, no se admite la vinculación profunda. Debe utilizar los vínculos universales Apple para la vinculación profunda a su aplicación o sitio Web.

## Vínculos universales {#section_F8147944679A42E59CF4FD8814E5EF12}

Los vínculos universales permiten conectarse a vínculos profundos en la aplicación iOS y son compatibles con iOS 9.2 o posterior. Cuando se accede a un vínculo universal, iOS redirige el vínculo directamente al vínculo profundo de la aplicación. Si su aplicación no está instalada, abre una URL para su sitio web en un navegador en su lugar. Para obtener más información acerca de los vínculos universales, consulte [Compatibilidad con vínculos universales](https://developer.apple.com/library/content/documentation/General/Conceptual/AppSearch/UniversalLinks.html).

## Vínculos de aplicación

Los vínculos de aplicación le permiten conectarse a vínculos profundos en su aplicación Android y es compatible con Android 6.0 o posterior. Cuando se accede a un vínculo de aplicación, Android redirige el vínculo directamente al vínculo profundo de la aplicación. Si su aplicación no está instalada, abre una URL para su sitio web en un navegador en su lugar. For more information about App Links, see the [Handling Android App Links](https://developer.android.com/training/app-links/index.html).

## Crear un vínculo de marketing mediante un vínculo universal o de aplicación {#section_609ADEFFB9B441C4A8C45E936D0DC859}

Puede crear un vínculo de marketing que utilice un vínculo universal o de aplicación.

### Configurar un vínculo universal

1. Para configurar vínculos universales en la aplicación iOS, vaya [a Gestión de vínculos universales en Apple](https://developer.apple.com/documentation/uikit/inter-process_communication/allowing_apps_and_websites_to_link_to_your_content/handling_universal_links).

2. En Adobe Mobile Services, configure los documentos de asociación de sitios:

   a. En la página de inicio de Mobile Services, seleccione la aplicación para la que desea configurar los vínculos universales.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Asegúrese de que la aplicación de iOS que gestiona los vínculos universales se agrega a la sección **[!UICONTROL Agregar aplicaciones]** de tiendas de aplicaciones.

   >[!TIP]
   >
   >Si la sección **[!UICONTROL Agregar aplicaciones]** de tiendas de aplicaciones no se muestra, haga clic en el vínculo **[!UICONTROL Agregar aplicación]** de App Store.

   d. En la sección Opciones **[!UICONTROL de vínculos universales y de aplicación, seleccione]** una aplicación de iOS y escriba el ID de la aplicación.

   f. Haga clic **[!UICONTROL en Guardar]**.

   Debe proporcionar al menos una selección de aplicación de iOS y un ID de aplicación, o recibirá un error.

   >[!IMPORTANT]
   >
   >Para actualizar los documentos, haga clic en la opción Actualizar de la sección Opciones de los vínculos universales y de la aplicación. However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Uso de un vínculo universal

1. En Adobe Mobile Services, cree un vínculo de marketing que utilice vínculos universales:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Haga clic **[!UICONTROL en Crear nuevo]**.

   c. Under **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Use Universal Links or App Links]**.

   d. Si ha configurado los documentos de asociación de sitios en *la* sección Configuración de documentos de asociación de sitios de Adobe Mobile Services, esta opción está seleccionada de forma predeterminada.

   Si no ha configurado los documentos, la opción **[!UICONTROL Utilizar vínculos universales o vínculos]** de aplicación está desactivada y **[!UICONTROL la opción Utilizar intersticiales]** está seleccionada de forma predeterminada.

   e. Si la opción **[!UICONTROL Utilizar vínculos universales o vínculos]** de aplicación está seleccionada, se muestra el **[!UICONTROL campo Ruta]** personalizada.

   Aquí los usuarios pueden definir la ruta de URL después del dominio, así como parámetros de consulta. Por ejemplo, si escribe `my/universal/link?os=9.2`, se convierte en la URL completa del vínculo de marketing `https://[marketing link domain]/my/universal/link?[AMS default query parameters]&os=9.2`.

   f. Haga clic en la ficha **[!UICONTROL Decisiones]** y configure el árbol de decisión.

   h. Si la aplicación de iOS está instalada, la aplicación gestiona el enlace profundo con su lógica. El destino final solo sirve como alternativa cuando la aplicación no está instalada. Como la aplicación no está instalada, el destino final solo puede ser un vínculo web o una tienda de aplicaciones.

   i. Haga clic **[!UICONTROL en Guardar]**.

>[!TIP]
>
>Una vez guardado el Vínculo de marketing, las Opciones de vínculos de marketing no se pueden modificar. Esto se debe a que no desea cambiar el comportamiento de los vínculos de marketing que pueden haberse distribuido.


### Configurar un vínculo de aplicación

1. Para configurar vínculos de aplicación en su aplicación Android, vaya a [Agregar vínculos de aplicación de Android](https://developer.android.com/studio/write/app-link-indexing).

1. En Adobe Mobile Services, configure los documentos de asociación de sitios:

   a. En la página de inicio de Mobile Services, seleccione la aplicación para la que desea configurar los vínculos de aplicación.

   b. Click **[!UICONTROL Manage App Settings]**.

   c. Asegúrese de que la aplicación de Android que gestiona los vínculos universales o los vínculos de aplicación se añade a la sección **[!UICONTROL Agregar aplicaciones]** de tiendas de aplicaciones.

   >[!TIP]
   >
   >If this section does not display, click the **[!UICONTROL Add App Store App]** link.

   d. Desplácese hasta la **[!UICONTROL sección Opciones]** de vínculos universales y de aplicación.

   e. Haga clic en la **[!UICONTROL ficha Vínculos de aplicación (Android)]** .

   f. Seleccione una aplicación de Android y escriba una huella de certificado SHA -256.

   g. Haga clic **[!UICONTROL en Guardar]**.

   Debe proporcionar al menos una selección de la aplicación Android y un certificado SHA -256, o recibirá un error.

   >[!IMPORTANT]
   >
   >Para actualizar los documentos, haga clic en la opción **[!UICONTROL Actualizar]** de la sección **Opciones de los vínculos universales y de la aplicación[!UICONTROL .]** However, when you click **[!UICONTROL Update]**, a warning notifies you that all Universal Links or App Links that you created in the past will be affected.

### Uso de un vínculo de aplicación

1. En Adobe Mobile Services, cree un vínculo de marketing que utilice vínculos de aplicación:

   a. Select the app from the Mobile Services home page, click **[!UICONTROL Acquisition]** &gt; **[!UICONTROL Marketing Link Builder]**.

   b. Haga clic **[!UICONTROL en Crear nuevo]**.

   c. En la sección **[!UICONTROL Opciones]** de vínculo de marketing, seleccione **[!UICONTROL Utilizar vínculos universales o vínculos de aplicación]**.

   d. Si ha configurado los documentos de asociación de sitios del paso 2, esta opción está seleccionada de forma predeterminada.

   If not, the **[!UICONTROL Use Universal Links or App Links]** option is disabled, and **[!UICONTROL Use Interstitials]** is selected by default.

   e. Si **[!UICONTROL se selecciona Utilizar vínculos universales o vínculos]** de aplicación, se muestra el **[!UICONTROL campo Ruta]** personalizada.

   Aquí los usuarios pueden definir la ruta de URL después del dominio, así como parámetros de consulta. Por ejemplo, si escribe `my/app/link?os=6.0`, se convierte en la URL completa del vínculo de marketing `https://[marketing link domain]/my/app/link?[AMS default query parameters]&os=6.0`.

   f. Haga clic en la ficha **[!UICONTROL Decisiones]** y configure el árbol de decisión.

   g. Si la aplicación de Android está instalada, la aplicación gestiona el enlace profundo con su lógica.

   El destino final solo sirve como caso de reserva para cuando la aplicación no está instalada. Como la aplicación no está instalada, el destino final solo puede ser un vínculo web o una tienda de aplicaciones.

   h. Haga clic **[!UICONTROL en Guardar]**.

>[!TIP]
>
>After a Marketing Link is saved, the **[!UICONTROL Marketing Links Options]** cannot be altered. Esto se debe a que no desea cambiar el comportamiento de los vínculos de marketing que pueden haberse distribuido.

## Uso de vínculos de marketing

Ahora puede utilizar estos vínculos de marketing en mensajes y otras áreas de la aplicación.

>[!IMPORTANT]
>
>No verá recuentos de rastreo de clics con vínculos universales o de aplicación, y tampoco podrá utilizar intersticiales.

