---
description: El informe Rutas de acción se basa en el análisis de las rutas y muestra un gráfico que representa las rutas que han pasado de un estado a otro en la aplicación.
keywords: móvil
seo-description: El informe Rutas de acción se basa en el análisis de las rutas y muestra un gráfico que representa las rutas que han pasado de un estado a otro en la aplicación.
seo-title: Informe de rutas de acción
solution: Marketing Cloud, Analytics
title: Informe de rutas de acción
topic: Informes, métricas
uuid: a 21 e 5 d 9 e-fd 57-4178-9 d 64-87181 b 7 f 988 b b
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Informe de rutas de acción{#action-paths}

El informe Rutas de acción se basa en el análisis de las rutas y muestra un gráfico que representa las rutas que han pasado de un estado a otro en la aplicación.

Los informes **[!UICONTROL Ver rutas]** y **Rutas de acción]son informes de rutas.[!UICONTROL ** El informe **[!UICONTROL Ver rutas]permite ver cómo navegan los usuarios en la aplicación de una pantalla a otra.** El informe **[!UICONTROL Ver acciones]muestra la secuencia de acciones y eventos, como clics, selecciones, cambios de tamaño, etc., que los usuarios realizan en la aplicación.**

>[!TIP]
>
>Puede utilizar un informe de canal para combinar la navegación y las acciones en un informe. For more information, see [Funnel](/help/using/usage/reports-funnel.md).

![](assets/action_paths.png)

Cada nodo, que es similar a una caja, representa un estado en las rutas de los usuarios a través de una aplicación. Por ejemplo, en el gráfico anterior, el nodo principal representa el número de usuarios que han iniciado la aplicación y luego han seleccionado una fotografía de la galería.

Si desea ver las opciones para modificar el gráfico, haga clic en un nodo y luego en **[!UICONTROL Enfocar]** o **[!UICONTROL Expandir]**. Por ejemplo, si hace clic en el estado **[!UICONTROL PhotoPicked]** del nodo principal, aparecen los iconos **[!UICONTROL Enfocar]y** Expandir **.**

![](assets/action_paths_icons.png)

To expand, click the **[!UICONTROL +]** icon. Esta opción muestra las rutas adicionales que llegan al nodo o salen de él. En el gráfico siguiente, el estado 1 inicia la aplicación, el estado 2 elige una fotografía (el elemento que expandió anteriormente) y el estado 3 incluye las distintas rutas que tomaron los usuarios:

* Seleccionar un elemento
* Agregar un elemento
* Arrastrar un elemento
* Escalar un elemento

La expansión de un estado es similar a un canal.

![ruta de acción expandir](assets/action_paths_expand.png)

To isolate the node and show paths that come into, and go out of the selected node, click the  ![focus icon](assets/icon_focus.png) icon. En el gráfico de abajo, las rutas siguientes se completaron **antes** de que los usuarios seleccionaran una foto:

* Girar un elemento
* Escalar un elemento
* Arrastrar un elemento
* Eliminar un elemento

De los usuarios que seleccionaron una foto, las rutas siguientes se completaron **después** de que se realizara esta acción:

* Seleccionar un elemento
* Agregar un elemento
* Arrastrar un elemento
* Escalar un elemento

![enfoque de ruta de acción](assets/action_paths_focus.png)

Puede enfocar o expandir varios nodos para obtener una vista detallada de las rutas que siguen los usuarios en la aplicación. Por ejemplo:

![ruta de acción múltiple](assets/action_paths_mult.png)

Para este informe, puede configurar las siguientes opciones:

* **[!UICONTROL Período de tiempo]**

   Haga clic en el icono de **[!UICONTROL calendario]para seleccionar un período de tiempo personalizado o elegir un período de tiempo preestablecido en la lista desplegable.**

* **[!UICONTROL Personalizar]**

   Customize your reports by changing the **[!UICONTROL Show By]** options, adding metrics and filters, and adding additional series (metrics), and more. For more information, see [Customize reports](/help/using/usage/reports-customize/reports-customize.md).

* **[!UICONTROL Filtro]**

   Haga clic en **[!UICONTROL Filtro]para crear un filtro que incluya distintos informes con el fin de ver el comportamiento de un segmento en todos los informes móviles.** Un filtro adhesivo permite definir un filtro que se aplica a todos los informes sin rutas. Para obtener más información, consulte [Adición de un filtro adhesivo](/help/using/usage/reports-customize/t-sticky-filter.md).

* **[!UICONTROL Descargar]**

   Click **[!UICONTROL PDF]** or **[!UICONTROL CSV]** to download or open documents and share with users who do not have access to Mobile Services or to use the file in presentations.