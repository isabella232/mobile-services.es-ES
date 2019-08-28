---
description: Puede crear y gestionar puntos de interés, los cuales permiten definir ubicaciones geográficas que puede utilizar para fines de correlación o para dirigir los mensajes en la aplicación, entre otras opciones. Al enviar una visita en un punto de interés, este se adjunta a la visita.
keywords: móvil
seo-description: Puede crear y gestionar puntos de interés, los cuales permiten definir ubicaciones geográficas que puede utilizar para fines de correlación o para dirigir los mensajes en la aplicación, entre otras opciones. Al enviar una visita en un punto de interés, este se adjunta a la visita.
seo-title: Administrar puntos de interés
solution: Marketing Cloud, Analytics
title: Administrar puntos de interés
topic: Métricas
uuid: 7 b 362534-54 fb -43 a 3-b 6 b 2-dfc 8 f 45 ff 7 c 6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

Puede crear y administrar puntos de interés, que le permiten definir ubicaciones geográficas que puede utilizar para fines de correlación, dirigir con mensajes en la aplicación, etc. Cuando se envía una visita en un punto de interés, el punto de interés se adjunta a la visita.

Para poder utilizar la ubicación, compruebe los siguientes requisitos:

* Debe tener Analytics - Aplicaciones móviles o Analytics Premium.
* Debe activar los **[!UICONTROL informes de ubicación]en la aplicación.**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. En la página Administrar puntos de interés, cuando hace clic **[!UICONTROL en Guardar]**, los cambios se empaquetan en la lista **[!UICONTROL Puntos de interés]** y el archivo de configuración de la aplicación activa se actualiza. Al guardar, también se actualiza la lista de puntos de la aplicación en los dispositivos de usuario, siempre y cuando la aplicación utilice el SDK y la configuración actualizados con una URL de punto de interés remoto.

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

Para utilizar la ubicación, realice las tareas siguientes:

1. Haga clic en el nombre de la aplicación para ir a la página Administrar configuración de aplicación correspondiente.
1. Click **[!UICONTROL Location]** &gt; **[!UICONTROL Manage Points of Interest]**.

   ![Resultado de los pasos](assets/poi.png)

1. Escriba la información en cada uno de los campos siguientes:

   * **[!UICONTROL Nombre de punto]**

      Escriba el nombre del **[!UICONTROL punto de ubicación.]**

      Podría ser el nombre de una ciudad o región. También puede crear un **[!UICONTROL punto de interés]para ubicaciones específicas, como recintos deportivos o empresas.**

   * **[!UICONTROL Latitud]**

      Escriba la latitud del **[!UICONTROL punto de interés]**. Puede buscar esta información en otras fuentes, como Internet.

   * **[!UICONTROL Longitud]**

      Escriba la longitud del **[!UICONTROL punto de interés]**. Puede buscar esta información en otras fuentes, como Internet.

   * **[!UICONTROL Radio (metros)]**

      Especifique el radio (en metros) alrededor del **[!UICONTROL punto de ubicación]que desea incluir.** Por ejemplo, si crea un punto de interés para Denver, Colorado, puede especificar un radio lo suficientemente grande como para incluir la ciudad de Denver y las zonas circundantes, pero excluyendo Colorado Springs.

   * **[!UICONTROL Icono de mapa]**

      Seleccione un icono que se mostrará en los informes [Información general](/help/using/location/c-location-overview.md) y [Mapa](/help/using/location/c-map-points.md) .

1. Agregue puntos de interés adicionales, según sea necesario.

   Le recomendamos que no agregue más de 5000 puntos de interés. Si agrega más de 5000 puntos de interés, puede guardarlos, pero recibirá un mensaje de advertencia que le avisará de que lo más recomendable es tener menos de 5000.

1. Haga clic en **[!UICONTROL Guardar]**.

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.
