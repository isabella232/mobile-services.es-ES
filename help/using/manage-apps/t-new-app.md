---
description: Puede usar esta información para crear una nueva aplicación y configurar sus métricas clave; configurar las opciones del SDK para Adobe Analytics y Adobe Audience Manager; configurar las opciones de adquisición y servicio de ID; así como descargar el archivo de configuración, los SDK y las herramientas para el desarrollador y el evaluador.
keywords: móvil
seo-description: Puede usar esta información para crear una nueva aplicación y configurar sus métricas clave; configurar las opciones del SDK para Adobe Analytics y Adobe Audience Manager; configurar las opciones de adquisición y servicio de ID; así como descargar el archivo de configuración, los SDK y las herramientas para el desarrollador y el evaluador.
seo-title: Agregar nueva aplicación
solution: Marketing Cloud, Analytics
title: Agregar nueva aplicación
topic: Métricas
uuid: 706 b 5 e 4 d -1318-4 a 9 e -8 c 69-ffabf 51 fa 02 c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Agregar nueva aplicación{#add-a-new-app}

Puede usar esta información para crear una nueva aplicación y configurar sus métricas clave; configurar las opciones del SDK para Adobe Analytics y Adobe Audience Manager; configurar las opciones de adquisición y servicio de ID; así como descargar el archivo de configuración, los SDK y las herramientas para el desarrollador y el evaluador.

Estas instrucciones le ayudarán a añadir una aplicación nueva y a configurar las integraciones de Adobe Analytics y Adobe Audience Manager.

Para poder configurar la aplicación, primero debe agregarla en la interfaz de usuario de Adobe Mobile Services. Después de crear la aplicación, se genera la configuración correcta y puede suministrársela a los desarrolladores que implementan el SDK de Mobile para la aplicación.

1. Inicie sesión en Adobe Mobile Services y realice una de las tareas siguientes:

   * Haga clic en **[!UICONTROL Crear nueva]para crear una aplicación.**
   * Para crear aplicaciones adicionales, haga clic en Administrar aplicaciones en el menú de navegación de la izquierda y luego haga clic en **[!UICONTROL Agregar]**.

      Para obtener más información sobre cómo iniciar sesión, consulte [Iniciar sesión](/help/using/gs/gs-signin.md).

      >[!TIP]
      >
      >Para administrar las aplicaciones existentes, haga clic en Administrar aplicaciones en el menú de navegación de la izquierda y haga clic en la aplicación que desee modificar. Puede hacer cambios en la página Información de la aplicación.

1. Rellene los campos siguientes:

   **[!UICONTROL Grupo de informes]**

   Especifique el grupo de informes en el que se recopilan y se almacenan los datos de los informes en Adobe Analytics. Cada aplicación está conectada a un grupo de informes de Analytics. Si está enviando datos de aplicación a varios grupos de informes, agregue una aplicación nueva por cada grupo de informes. Cada aplicación está conectada a un grupo de informes de Analytics. Si está enviando datos de aplicación a varios grupos de informes, agregue una aplicación nueva por cada grupo de informes.

   Si se le han otorgado privilegios de administrador de Analytics en Adobe Mobile, puede crear un nuevo grupo de informes en Adobe Mobile. To create a new report suite, select **[!UICONTROL New Report Suite]** and type information into the following fields:

   * **[!UICONTROL ID del grupo de informes]**

      Este ID identifica exclusivamente el grupo de informes en Adobe Analytics. El prefijo de la empresa se agrega automáticamente al principio del ID.

   * **[!UICONTROL Copiar ajustes de]**

      Las variables, los eventos, las reglas de procesamiento y otros ajustes se configuran en el nuevo grupo de informes exactamente igual que en este grupo de informes. Un grupo de informes creado en Mobile Services solo está disponible sin conexión (o marcado con hora) si el grupo de informes **Copiar ajustes de** que se ha usado es la plantilla de aplicación móvil, o si se crea un grupo de informes disponible sin conexión.

   * **[!UICONTROL Huso horario]**

      Todas las fechas de los informes están en esta zona horaria. Este ajuste intenta usar una zona horaria más cercana a la que usa su explorador.

   * **[!UICONTROL Moneda]**

      Los ingresos se registran y se registran como este tipo de moneda.
   >[!TIP]
   >
   >Para utilizar un grupo de informes virtuales (VRS), consulte [Grupos de informes virtuales](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL Icono]**

      (**Optional**) To browse to and select an icon for your app, click **[!UICONTROL Icon]**.

   * **[!UICONTROL Nombre]**

      (**Optional**) Type a descriptive name for the app. Este nombre le ayuda a localizar rápidamente una aplicación y un nombre significativo puede ayudarle a comprender rápidamente el propósito y la configuración de la aplicación.

   * **[!UICONTROL Tipo]**

      Seleccione un tipo en la lista desplegable. Los informes disponibles que se muestran en el menú de navegación de la izquierda pueden variar en función del tipo de aplicación que seleccione.

      Estos son los tipos disponibles:

      * **[!UICONTROL Standard]**

         You can leave the **[!UICONTROL Standard}** option selected for most apps.

      * **[!UICONTROL Publicación]**

         Puede seleccionar esta opción si su aplicación se creó con Adobe Digital Publishing Suite.

      * **[!UICONTROL Juego]**

         Esta opción se parece a **[!UICONTROL Estándar]**, con la diferencia de que **Juego]actualiza la terminología usada en los informes por términos de este campo.[!UICONTROL ** Por ejemplo, los usuarios se cambian a reproductores. Los informes específicos de juegos se muestran automáticamente en las aplicaciones de juegos.
   * **[!UICONTROL Descripción]**

      (**Optional**) Type a description for the app.



1. Click **[!UICONTROL Save]** to add the new app.

   Después de agregar la aplicación, puede consultar la página Información de la aplicación para ver cómo configurar otras opciones. For more information, see [Manage App Settings](/help/using/c-manage-app-settings/c-manage-app-settings.md).
