---
description: Puede crear o editar vínculos de marketing para proporcionar vínculos profundos a su aplicación móvil o sitio web.
keywords: móvil
solution: Experience Cloud Services,Analytics
title: Crear o editar vínculos de marketing
topic-fix: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
exl-id: a9b5c98d-77c1-4a40-96e5-f9e234d55ec5
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 96%

---

# Crear o editar vínculos de marketing {#create-or-edit-marketing-links}

Puede crear o editar vínculos de marketing para proporcionar vínculos profundos a su aplicación móvil o sitio web. Para obtener más información, consulte [Vínculos universales de Apple y de la aplicación de Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. En el panel de navegación de la izquierda de su aplicación, expanda **[!UICONTROL Adquisición]** y luego haga clic en **[!UICONTROL Generador de vínculos de marketing]**.
1. Complete una de las siguientes tareas:

   * Para crear un nuevo vínculo de marketing, haga clic en **[!UICONTROL Crear nuevo]**.
   * Para editar un vínculo, haga clic en el nombre del vínculo en la columna **[!UICONTROL Título]**.

1. Rellene los campos siguientes:

   * **[!UICONTROL Nombre del vínculo de marketing]**:

      (**Necesario**) Especifique un nombre descriptivo para el vínculo de marketing. El nombre solo aparece en la página Vínculos de marketing de la interfaz de usuario de Adobe Mobile Services. Un nombre descriptivo le ayuda a usted y a otras personas de su organización a encontrar rápidamente vínculos específicos y puede proporcionar información sobre su finalidad.

   * **[!UICONTROL Código de seguimiento único]**:

      (**Necesario**) Especifique el código de seguimiento deseado o haga clic en ( ![generar icono](assets/icon_generate.png) ) para crear un nuevo código de seguimiento. Puede ver informes que detallen el uso del código de seguimiento.

   * **[!UICONTROL Agregar datos de contexto de seguimiento]**:

      (**Opcional**) Haga clic en el icono **[!UICONTROL +]** y escriba los datos relevantes para hacer un seguimiento de la campaña usando datos de contexto. En la lista desplegable **[!UICONTROL Personalizar datos de contexto]**, seleccione una etiqueta preestablecida o una de las suyas. Los datos de contexto se utilizan para realizar un informe cuando se implementa el vínculo de marketing.

      Las siguientes etiquetas preestablecidas están disponibles:

      * **Datos de contexto personalizados** Especifique la clave y el valor. Si agrega datos de contexto personalizados, debe crear una regla de procesamiento. Para obtener más información, consulte [Información general sobre las reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) en la documentación de Adobe Analytics.

      * **Origen** Especifique el referente original, como “newsletter” o “página principal”.

      * **Medio** Especifique el medio de marketing (por ejemplo, “banner” o “correo electrónico”).

      * **Contenido** Especifique el nombre o el ID de la publicidad con el vínculo.

      * **Término** Especifique los términos de pago u otros términos de búsqueda de la publicidad.
1. Haga clic en **[!UICONTROL Guardar]**.
1. Rellene los campos siguientes:

   * **(Obligatorio)** En **[!UICONTROL URL alternativa]**, especifique la URL a la que se dirige a los usuarios cuando un destino no coincide (por ejemplo, si el usuario está en un escritorio o en otra plataforma que no coincide con una regla de destino).
   * En **[!UICONTROL Opciones del vínculo de marketing]**, seleccione **[!UICONTROL Intersticiales]** o **[!UICONTROL Vínculos universales y de aplicación]**.

      Para obtener más información, consulte [Intersticiales](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) o Vínculos universales de [Apple y Vínculos de aplicación de Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Condicional)** Si **[!UICONTROL Vínculos universales y de aplicación]** está seleccionado, los usuarios pueden definir la ruta de la URL después del dominio con cualquier parámetro de consulta en **[!UICONTROL Ruta personalizada]**. Para obtener más información, consulte [Vínculos universales de Apple y de la aplicación de Android](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Haga clic en **[!UICONTROL Editar intersticial de vínculo profundo]** y configure el vínculo.

   (**Opcional**) Cuando hay varios destinos, los usuarios pueden ser redirigidos en función de si tienen una aplicación móvil instalada. Si la aplicación está instalada, se visualiza una página de aterrizaje intersticial.

   Para obtener más información, consulte la [Elementos intersticiales](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Haga clic en **[!UICONTROL Guardar]** y en **[!UICONTROL Siguiente]**.
1. En la página Destino, configure el vínculo.

   1. Haga clic en el icono **[!UICONTROL Decisión]** ( ![icono de decisión](assets/icon_decision.png) ) seleccione una de las siguientes ubicaciones de decisión:

      * **[!UICONTROL Agregar decisión]**
      * **[!UICONTROL Agregar ruta]**
   1. Si ha elegido **[!UICONTROL Agregar decisión]**, seleccione uno de los siguientes tipos de decisión:

      * **[!UICONTROL Decisión operativa]**

         Los sistemas operativos admitidos son iOS, Android, AMX, etc.

      * **[!UICONTROL Device Type]**

         Los tipos de dispositivos incluyen equipos de escritorio, lectores electrónicos, consolas de juego, teléfonos móviles, descodificadores de Internet, etc.
   1. Haga clic en el icono **[!UICONTROL Destino]** ( ![icono cuadrado](assets/icon_square.png) ) y seleccione uno de los siguientes tipos de destino:

      * **[!UICONTROL Tienda de aplicaciones]**
      * **[!UICONTROL Vínculo web]**
      * **[!UICONTROL Vínculo profundo de la aplicación]**
      * **[!UICONTROL Vínculo híbrido]**

      >[!TIP]
      >
      >Al usar el tipo de destino **[!UICONTROL Vínculo web]** con un vínculo a la tienda de aplicaciones, no se realiza un seguimiento de la adquisición. Para hacer un seguimiento de las adquisiciones, use el tipo de destino **[!UICONTROL Tienda de aplicaciones]**.

      Para obtener más información, consulte [Creación de un nuevo destino de vínculo](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Para guardar el vínculo de marketing, haga clic en ![elipses](assets/icon_elipses.png) y, a continuación, en **[!UICONTROL Guardar]**.
