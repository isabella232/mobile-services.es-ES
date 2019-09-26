---
description: Puede crear o editar vínculos de marketing para proporcionar vínculos profundos en la aplicación móvil o en el sitio web.
keywords: móvil
seo-description: Puede crear o editar vínculos de marketing para proporcionar vínculos profundos en la aplicación móvil o en el sitio web.
seo-title: Crear o editar vínculos de marketing
solution: Marketing Cloud,Analytics
title: Crear o editar vínculos de marketing
topic: Métricas
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

You can create or edit Marketing Links to provide deep linking to your mobile app or your website. Para obtener más información, consulte [Apple Universal Links y Android App Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. Complete una de las siguientes tareas:

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * Para editar un vínculo, haga clic en el nombre del vínculo en la columna **[!UICONTROL Título].**

1. Rellene los campos siguientes:

   * **[!UICONTROL Nombre del vínculo de marketing]**:

      (**Required**) Specify a descriptive name for your Marketing Link. El nombre solo aparece en la página Vínculos de marketing de la interfaz de usuario de Adobe Mobile Services. Un nombre descriptivo le ayuda a usted y a otras personas de su organización a encontrar rápidamente vínculos específicos y puede proporcionar información sobre su finalidad.

   * **[!UICONTROL Código de seguimiento único]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. Puede ver informes que detallen el uso del código de seguimiento.

   * **[!UICONTROL Agregar datos de contexto de seguimiento]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. En la lista desplegable **[!UICONTROL Personalizar datos de contexto], seleccione una etiqueta preestablecida o una de las suyas.** Los datos de contexto se utilizan para generar informes cuando se implementa Marketing Link.

      Las siguientes etiquetas preestablecidas están disponibles:

      * **Datos** de contexto personalizados Especifique la clave y el valor. Si agrega datos de contexto personalizados, debe crear una regla de procesamiento. Para obtener más información, consulte Introducción a las reglas [de procesamiento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

      * **Origen** Especifique el referente original, como "newsletter" o "página principal".

      * **Medium
Specify the marketing medium, such as "banner" or "email."**

      * **Content
Specify the name or ID of the ad with the link.**

      * **Term
Specify paid terms or other search terms for the ad.**
1. Haga clic en **[!UICONTROL Guardar]**.
1. Rellene los campos siguientes:

   * **(Requerido)** En URL de **[!UICONTROL reserva]**, especifique la dirección URL a la que se dirige a los usuarios cuando un destino no coincide (por ejemplo, si el usuario está en un escritorio u otra plataforma que no coincide con una regla de destino).
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      For more information, see Interstitials or Apple Universal Links and Android App Links.[](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md)[](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)

   * **(Condicional)** Si se selecciona Vínculos **** universales o de aplicación, en Ruta **** personalizada, los usuarios pueden definir la ruta de URL después del dominio con cualquier parámetro de consulta. For more information, see Apple Universal Links and Android App Links.[](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md)

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. Si la aplicación está instalada, se abre una página de inicio intersticial.

   Para obtener más información, consulte [Intersticiales](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Click **[!UICONTROL Save]** and click **[!UICONTROL Next]**.
1. En la página Destino, configure el vínculo.

   1. Click the **[!UICONTROL Decision]** icon (![decision icon](assets/icon_decision.png)) and select one of the following decision locations:

      * **[!UICONTROL Agregar decisión]**
      * **[!UICONTROL Agregar ruta]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL Decisión operativa]**

         Los sistemas operativos admitidos son iOS, Android, AMX, etc.

      * **[!UICONTROL Tipo de dispositivo]**

         Los tipos de dispositivos incluyen equipos de escritorio, lectores electrónicos, consolas de juego, teléfonos móviles, descodificadores de Internet, etc.
   1. Click the **[!UICONTROL Destination]** icon ( ![square icon](assets/icon_square.png) ) and select one of the following destination types:

      * **[!UICONTROL Tienda de aplicaciones]**
      * **[!UICONTROL Vínculo web]**
      * **[!UICONTROL Vínculo profundo de la aplicación]**
      * **[!UICONTROL Vínculo híbrido]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. Para hacer un seguimiento de las adquisiciones, use el tipo de destino **[!UICONTROL Tienda de aplicaciones].**

      For more information, see Create a new link destination.[](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md)




1. To save the Marketing Link, click elipses and then Save.![](assets/icon_elipses.png)****
