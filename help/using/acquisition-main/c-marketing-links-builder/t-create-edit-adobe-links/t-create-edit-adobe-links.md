---
description: Puede crear o editar vínculos de marketing para proporcionar vínculos profundos a su aplicación móvil o a su sitio web.
keywords: móvil
seo-description: Puede crear o editar vínculos de marketing para proporcionar vínculos profundos a su aplicación móvil o a su sitio web.
seo-title: Crear o editar vínculos de marketing
solution: Marketing Cloud, Analytics
title: Crear o editar vínculos de marketing
topic: Métricas
uuid: 305 a 8265-38 de -4 d 19-8 c 79-b 3912 f 5 aae 7 c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

Puede crear o editar vínculos de marketing para proporcionar vínculos profundos a su aplicación móvil o a su sitio web. Para obtener más información, consulte [Vínculos universales Apple y vínculos de aplicaciones Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. Complete una de las siguientes tareas:

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * Para editar un vínculo, haga clic en el nombre del vínculo en la columna **[!UICONTROL Título].**

1. Rellene los campos siguientes:

   * **[!UICONTROL Nombre del vínculo de marketing]**:

      **(Necesario**) Especifique un nombre descriptivo para el vínculo de marketing. El nombre solo aparece en la página Vínculos de marketing de la interfaz de usuario de Adobe Mobile Services. Un nombre descriptivo le ayuda a usted y a otras personas de su organización a encontrar rápidamente vínculos específicos y puede proporcionar información sobre su finalidad.

   * **[!UICONTROL Código de seguimiento único]**:

      **(Necesario**) Especifique el código de seguimiento deseado o haga clic (![genere un icono](assets/icon_generate.png) para crear un nuevo código de seguimiento. Puede ver informes que detallen el uso del código de seguimiento.

   * **[!UICONTROL Agregar datos de contexto de seguimiento]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. En la lista desplegable **[!UICONTROL Personalizar datos de contexto], seleccione una etiqueta preestablecida o una de las suyas.** Los datos de contexto se utilizan para generar informes cuando se implementa el vínculo de marketing.

      Las siguientes etiquetas preestablecidas están disponibles:

      * **Datos
de contexto personalizados** Especifique la clave y el valor. Si agrega datos de contexto personalizados, debe crear una regla de procesamiento. Para obtener más información, consulte [Descripción general de reglas de procesamiento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

      * **Fuente**
Especifique el referente original, como "boletín" o "página principal".

      * **Medio**
Especifique el medio de mercadotecnia, como «banner» o «correo electrónico».

      * **Contenido**
Especifique el nombre o ID del anuncio con el vínculo.

      * **Término**
Especifique los términos de pago u otros términos de búsqueda de la publicidad.
1. Haga clic en **[!UICONTROL Guardar]**.
1. Rellene los campos siguientes:

   * **(Requerido)** En **[!UICONTROL URL alternativa]**, especifique la URL a la que se dirige a los usuarios cuando un destino no coincide (por ejemplo, si el usuario está en un escritorio o en otra plataforma que no coincide con una regla de destino).
   * In **[!UICONTROL Marketing Link Options]**, select **[!UICONTROL Interstitials]** or **[!UICONTROL Universal and App Links]**.

      Para obtener más información, consulte [Intersticiales](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) o [Vínculos universales Apple y Vínculos de aplicación Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Condicional)** Si **[!UICONTROL los vínculos universales o de aplicación]** están **[!UICONTROL seleccionados]**, los usuarios pueden definir la ruta de URL después del dominio con cualquier parámetro de consulta. Para obtener más información, consulte [Vínculos universales Apple y vínculos de aplicaciones Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

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

      Para obtener más información, consulte [Creación de un nuevo destino de vínculo](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Para guardar el vínculo de marketing, haga clic ![en elipses](assets/icon_elipses.png) y **[!UICONTROL luego en Guardar]**.
