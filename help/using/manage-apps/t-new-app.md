---
description: Puede usar esta información para crear una nueva aplicación y configurar sus métricas clave; configurar las opciones del SDK para Adobe Analytics y Adobe Audience Manager; configurar las opciones de adquisición y servicio de ID; así como descargar el archivo de configuración, los SDK y las herramientas para el desarrollador y el evaluador.
keywords: móvil
seo-description: Puede usar esta información para crear una nueva aplicación y configurar sus métricas clave; configurar las opciones del SDK para Adobe Analytics y Adobe Audience Manager; configurar las opciones de adquisición y servicio de ID; así como descargar el archivo de configuración, los SDK y las herramientas para el desarrollador y el evaluador.
seo-title: Agregar nueva aplicación
solution: Experience Cloud,Analytics
title: Agregar nueva aplicación
topic: Métricas
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Agregar nueva aplicación{#add-a-new-app}

Puede usar esta información para crear una nueva aplicación y configurar sus métricas clave; configurar las opciones del SDK para Adobe Analytics y Adobe Audience Manager; configurar las opciones de adquisición y servicio de ID; así como descargar el archivo de configuración, los SDK y las herramientas para el desarrollador y el evaluador.

Estas instrucciones le ayudarán a añadir una aplicación nueva y a configurar las integraciones de Adobe Analytics y Adobe Audience Manager.

Para poder configurar la aplicación, primero debe agregarla en la interfaz de usuario de Adobe Mobile Services. Después de crear la aplicación, se genera la configuración correcta y puede suministrársela a los desarrolladores que implementan el SDK de Mobile para la aplicación.

1. Inicie sesión en Adobe Mobile Services y realice una de las tareas siguientes:

   * Haga clic en **[!UICONTROL Crear nueva]** para crear una aplicación.
   * Para crear aplicaciones adicionales, haga clic en Administrar aplicaciones en el menú de navegación de la izquierda y luego haga clic en **[!UICONTROL Agregar]**.

      Para obtener más información sobre cómo iniciar sesión, consulte [Iniciar sesión](/help/using/gs/gs-signin.md).

      >[!TIP]
      >
      >Para administrar las aplicaciones existentes, haga clic en Administrar aplicaciones en el menú de navegación de la izquierda y luego en la aplicación que desea modificar. Puede hacer cambios en la página Información de la aplicación.

1. Rellene los campos siguientes:

   **[!UICONTROL Grupo de informes]**

   Especifique el grupo de informes en el que se recopilan y se almacenan los datos de los informes en Adobe Analytics. Cada aplicación está conectada a un grupo de informes de Analytics. Si está enviando datos de aplicación a varios grupos de informes, agregue una aplicación nueva por cada grupo de informes. Cada aplicación está conectada a un grupo de informes de Analytics. Si está enviando datos de aplicación a varios grupos de informes, agregue una aplicación nueva por cada grupo de informes.

   Si se le han otorgado privilegios de administrador de Analytics en Adobe Mobile, puede crear un nuevo grupo de informes en Adobe Mobile. Para crear un nuevo grupo de informes, seleccione **[!UICONTROL Nuevo grupo de informes]** y rellene los siguientes campos:

   * **[!UICONTROL ID del grupo de informes]**

      Este ID identifica de forma exclusiva el grupo de informes en Adobe Analytics. El prefijo de la empresa se agrega automáticamente al principio del ID.

   * **[!UICONTROL Copiar configuración de]**

      Las variables, los eventos, las reglas de procesamiento y otros ajustes se configuran en el conjunto de informes nuevos igual que en este conjunto de informes. Un grupo de informes creado en Mobile Services solo está disponible sin conexión (o marcado con hora) si el grupo de informes **[!UICONTROL Copiar ajustes de]** que se ha usado es la plantilla de aplicación móvil, o si se crea un grupo de informes disponible sin conexión.

   * **[!UICONTROL Zona horaria]**

      Todas las fechas de los informes se encuentran en esta zona horaria. Este ajuste intenta usar una zona horaria más cercana a la que usa su explorador.

   * **[!UICONTROL Moneda]**

      Se hace un seguimiento de los ingresos y se generan informes en este tipo de moneda.
   >[!TIP]
   >
   >Para utilizar un grupo de informes virtuales (VRS), consulte [Grupos de informes virtuales](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL Icono]**

      (**Opcional**) Si desea buscar y seleccionar un icono para la aplicación, haga clic en el **[!UICONTROL Icono]**.

   * **[!UICONTROL Nombre]**

      (**Opcional**) Escriba un nombre descriptivo para la aplicación. Este nombre le ayuda a localizar rápidamente una aplicación, y un nombre significativo le ayuda a comprender rápidamente el propósito y la configuración de la aplicación.

   * **[!UICONTROL Tipo]**

      Seleccione un tipo en la lista desplegable. Los informes disponibles que se muestran en el menú de navegación de la izquierda pueden variar en función del tipo de aplicación que seleccione.

      Estos son los tipos disponibles:

      * **[!UICONTROL Standard]**

         Puede dejar seleccionada la opción **[!UICONTROL Standard}** para la mayoría de las aplicaciones.

      * **[!UICONTROL Publicación]**

         Puede seleccionar esta opción si su aplicación se creó con Adobe Digital Publishing Suite.

      * **[!UICONTROL Juego]**

         Esta opción se parece a **[!UICONTROL Estándar]**, con la diferencia de que **[!UICONTROL Juego]** actualiza la terminología usada en los informes por términos de este campo. Por ejemplo, “usuarios” se cambia a “jugadores”. Los informes específicos de juegos se muestran automáticamente en las aplicaciones de juegos.
   * **[!UICONTROL Descripción]**

      (**Opcional**) Escriba una descripción para la aplicación.



1. Haga clic en **[!UICONTROL Guardar]** para agregar la nueva aplicación.

   Después de agregar la aplicación, puede consultar la página Información de la aplicación para ver cómo configurar otras opciones. Para obtener más información, consulte [Administrar configuración de aplicación](/help/using/c-manage-app-settings/c-manage-app-settings.md).
