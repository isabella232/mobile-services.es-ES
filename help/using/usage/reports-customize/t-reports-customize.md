---
description: Esta información sirve para personalizar los informes integrados mediante la adición de filtros (segmentos) adicionales.
keywords: móvil
seo-description: Esta información sirve para personalizar los informes integrados mediante la adición de filtros (segmentos) adicionales.
seo-title: Añadir filtros a informes
solution: Experience Cloud,Analytics
title: Añadir filtros a informes
topic: Informes, métricas
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
translation-type: ht
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Añadir filtros a informes{#add-filters-to-reports}

Esta información sirve para personalizar los informes integrados mediante la adición de filtros (segmentos) adicionales.

>[!IMPORTANT]
>
>Las métricas de aplicación de móvil también están disponibles en los informes y análisis de marketing, los análisis específicos, el almacén de datos y otras interfaces de generación de informes de Analytics. Si un tipo de informe o desglose no está disponible en Adobe Mobile, se puede generar usando otra interfaz de generación de informes.

En este ejemplo, personalizaremos el informe **[!UICONTROL Usuarios y sesiones]**, pero las instrucciones sirven para cualquier informe.

1. Abra la aplicación y haga clic en **[!UICONTROL Uso]** &gt; **[!UICONTROL Usuarios y sesiones]**.

   ![](assets/customize1.png)

   En este informe se proporciona una vista de tiempo extra completa de nuestros usuarios de la aplicación. Sin embargo, las métricas para las dos versiones de iOS y Android de esta aplicación se recopilan en el mismo grupo de informes. Podemos segmentar a los usuarios por sistema operativo móvil agregando un filtro personalizado a la métrica Usuarios.

1. Haga clic en **[!UICONTROL Personalizar]**.

   ![](assets/customize2.png)

1. En **[!UICONTROL Usuarios]**, haga clic en **[!UICONTROL Añadir filtro]** y en **[!UICONTROL Añadir regla]**.

1. Seleccione **[!UICONTROL Sistema operativo]** y, en la lista desplegable, seleccione **[!UICONTROL iOS]**.

   ![](assets/customize3.png)

   Para agregar Android como filtro, debe repetir este paso.

1. Haga clic en **[!UICONTROL Y]**, seleccione **[!UICONTROL Sistemas operativos]** en la lista desplegable y elija **[!UICONTROL Android]**.

   Los filtros deberían tener un aspecto similar al siguiente ejemplo:

   ![](assets/customize4.png)

1. Haga clic en **[!UICONTROL Actualizar]**.
1. Para regenerar el informe, haga clic en **[!UICONTROL Ejecutar]**.

   Ahora, este informe muestra los usuarios desglosados por sistema operativo. El título del informe se ha modificado para que coincida con los filtros que se le han aplicado.

   ![](assets/customize5.png)

   Puede personalizar más este informe. Desde iOS 8.3, puede añadir la métrica Primeros lanzamientos con un filtro de versión del sistema operativo iOS 8.3 para ver cuántos clientes de iOS 8.3 han actualizado sus aplicaciones y han realizado un primer lanzamiento.
1. En **[!UICONTROL Primeros lanzamientos]**, haga clic en **[!UICONTROL Añadir filtro]** y en **[!UICONTROL Añadir regla]**, seleccione **[!UICONTROL Sistema operativo]** en la lista desplegable y elija **[!UICONTROL iOS]**.
1. Haga clic en **[!UICONTROL Y]**, seleccione **[!UICONTROL Versión del sistema operativo]** en la lista desplegable y elija **[!UICONTROL iOS 8.3]**.

   Los filtros deberían estar como en este ejemplo:

   ![](assets/customize6.png)

1. Haga clic en **[!UICONTROL Actualizar]** y **[!UICONTROL Ejecutar]**.

   Ahora, en este informe se muestran los usuarios con iOS 8.3 que han utilizado la aplicación por primera vez.

   ![](assets/customize7.png)

   Pruebe las diferentes opciones del menú de personalización del informe y no olvide agregar sus favoritos. Las direcciones URL de informes de Adobe Mobile son completamente funcionales y pueden enviarse por correo electrónico o agregarse a los favoritos.
