---
description: El informe Ver rutas, que se basa en el análisis de estas, muestra un gráfico que representa las rutas que pasaron de un estado a otro en la aplicación.
keywords: móvil
seo-description: El informe Ver rutas, que se basa en el análisis de estas, muestra un gráfico que representa las rutas que pasaron de un estado a otro en la aplicación.
seo-title: Ver informe de rutas
solution: Marketing Cloud, Analytics
title: Ver informe de rutas
topic: Informes, métricas
uuid: bc 73 edce -0 cc 0-4349-9 a 48-e 0 a 40 cbe 1 b 67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Ver informe de rutas {#view-paths}

El informe **[!UICONTROL Ver rutas], que se basa en el análisis de estas, muestra un gráfico que representa las rutas que pasaron de un estado a otro en la aplicación.**

>[!TIP]
>
>The **[!UICONTROL View Paths]** and **[!UICONTROL View Action]** reports are similar because both are pathing reports. El informe **[!UICONTROL Ver rutas]permite ver cómo navegan los usuarios en la aplicación de una pantalla a otra.** El informe **[!UICONTROL Ver acciones]muestra la secuencia de acciones y eventos, como clics, selecciones, cambios de tamaño, etc., que los usuarios realizan en la aplicación.** Puede utilizar un informe de canal para combinar la navegación y las acciones en un informe. For more information, see [Funnel](/help/using/usage/reports-funnel.md).

![ver rutas](assets/view_paths.png)

Cada nodo, que es similar a una caja, representa un estado en las rutas de los usuarios a través de una aplicación. Por ejemplo, en la ilustración anterior, el nodo principal representa el número de usuarios que han iniciado la aplicación y han navegado a la vista principal.

Cuando haga clic en un nodo para proporcionar las opciones adicionales que permiten modificar el gráfico, aparecerán iconos como **[!UICONTROL Enfocar]** o **Expandir[!UICONTROL .]** Por ejemplo, si hace clic en el estado **[!UICONTROL MainView]** del nodo principal, aparecen los iconos **[!UICONTROL Enfoque]y** Expandir **.**

To expand the view, click the **[!UICONTROL +]** icon to display the additional paths that come in to or go from the node. En la ilustración siguiente, el estado 1 inicia la aplicación, el estado 2 está viendo la página principal de la aplicación y el estado 3 incluye las siguientes rutas que tomaron los usuarios:

* Navegar al carrete
* Navegar al selector de elementos
* Navegar a la cámara
* Navegar a la página de información del elemento

![](assets/view_paths_expand.png)

Click ![focus icon](assets/icon_focus.png) to isolate the node and to show the paths that are coming into and going out of the selected node. En la ilustración de abajo, las rutas siguientes anteceden a los usuarios que estaban viendo la vista principal de la aplicación:

* Información del elemento
* Selector de elementos
* Carrete
* Cámara

![enfoque de ruta de visualización](assets/view_paths_focus.png)

Puede enfocar o expandir varios nodos para obtener una vista detallada de las rutas que siguen los usuarios en la aplicación. Por ejemplo:

![ver ruta múltiple](assets/view_paths_mult.png)

Para este informe, puede configurar las siguientes opciones:

* **[!UICONTROL Período de tiempo]** Haga clic en **[!UICONTROL el icono de calendario]** para seleccionar un período personalizado o seleccionar un período de tiempo preestablecido en la lista desplegable.
* **[!UICONTROL Personalice]**
personalizar los informes cambiando las **[!UICONTROL opciones Mostrar por]** , agregando métricas y filtros, agregando series (métricas) adicionales y más. For more information, see [Customize Reports](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filtro]**
Haga clic **[!UICONTROL en Filtro]** para crear un filtro que incluya distintos informes y ver cómo funciona un segmento en todos los informes móviles. Un filtro adhesivo permite definir un filtro que se aplica a todos los informes sin rutas. Para obtener más información, consulte [Agregar filtro adhesivo](/help/using/usage/reports-customize/t-sticky-filter.md).
* **[!UICONTROL Descargue]**
PDF o ******[!UICONTROL CSV]** para descargar o abrir documentos y compartir con usuarios que no tengan acceso a Mobile Services o para utilizar el archivo en presentaciones.