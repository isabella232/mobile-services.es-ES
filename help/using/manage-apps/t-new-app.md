---
description: Puede usar esta información para crear una nueva aplicación y configurar sus métricas clave; configurar las opciones del SDK para Adobe Analytics y Adobe Audience Manager; configurar las opciones de adquisición y servicio de ID; así como descargar el archivo de configuración, los SDK y las herramientas para el desarrollador y el evaluador.
keywords: móvil
seo-description: Puede usar esta información para crear una nueva aplicación y configurar sus métricas clave; configurar las opciones del SDK para Adobe Analytics y Adobe Audience Manager; configurar las opciones de adquisición y servicio de ID; así como descargar el archivo de configuración, los SDK y las herramientas para el desarrollador y el evaluador.
seo-title: Agregar nueva aplicación
solution: Marketing Cloud,Analytics
title: Agregar nueva aplicación
topic: Métricas
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
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

      For more information about signing in, see Sign in.[](/help/using/gs/gs-signin.md)

      >[!TIP]
      >
      >Para administrar las aplicaciones existentes, haga clic en Administrar aplicaciones en el menú de navegación de la izquierda y haga clic en la aplicación que desee modificar. Puede hacer cambios en la página Información de la aplicación.

1. Rellene los campos siguientes:

   **[!UICONTROL Grupo de informes]**

   Especifique el grupo de informes en el que se recopilan y se almacenan los datos de los informes en Adobe Analytics. Cada aplicación está conectada a un grupo de informes de Analytics. Si está enviando datos de aplicación a varios grupos de informes, agregue una aplicación nueva por cada grupo de informes. Cada aplicación está conectada a un grupo de informes de Analytics. Si está enviando datos de aplicación a varios grupos de informes, agregue una aplicación nueva por cada grupo de informes.

   Si se le han otorgado privilegios de administrador de Analytics en Adobe Mobile, puede crear un nuevo grupo de informes en Adobe Mobile. To create a new report suite, select **[!UICONTROL New Report Suite]** and type information into the following fields:

   * **[!UICONTROL ID del grupo de informes]**

      This ID uniquely identifies the report suite in Adobe Analytics. El prefijo de la empresa se agrega automáticamente al principio del ID.

   * **[!UICONTROL Copy Settings From]**

      Las variables, los eventos, las reglas de procesamiento y otras opciones de configuración se configuran en el nuevo grupo de informes de la misma manera que en este grupo de informes. Un grupo de informes creado en Mobile Services solo está disponible sin conexión (o marcado con hora) si el grupo de informes **Copiar ajustes de** que se ha usado es la plantilla de aplicación móvil, o si se crea un grupo de informes disponible sin conexión.

   * **[!UICONTROL Timezone]**

      Todas las fechas de informes están en este huso horario. Este ajuste intenta usar una zona horaria más cercana a la que usa su explorador.

   * **[!UICONTROL Moneda]**

      Los ingresos se rastrean y se registran como este tipo de moneda.
   >[!TIP]
   >
   >To use a virtual reporting suite (VRS), see Virtual Report Suites.[](/help/using/manage-apps/c-mob-vrs.md)

   * **[!UICONTROL Icono]**

      (**Optional**) To browse to and select an icon for your app, click **[!UICONTROL Icon]**.

   * **[!UICONTROL Nombre]**

      (**Optional**) Type a descriptive name for the app. This name helps you quickly locate an app, and a meaningful name can help you quickly understand the app's purpose and settings.

   * **[!UICONTROL Tipo]**

      Seleccione un tipo en la lista desplegable. Los informes disponibles que se muestran en el menú de navegación de la izquierda pueden variar en función del tipo de aplicación que seleccione.

      Estos son los tipos disponibles:

      * **[!UICONTROL Standard]**

         You can leave the **[!UICONTROL Standard}** option selected for most apps.

      * **[!UICONTROL Publicación]**

         Puede seleccionar esta opción si su aplicación se creó con Adobe Digital Publishing Suite.

      * **[!UICONTROL Juego]**

         Esta opción se parece a **[!UICONTROL Estándar]**, con la diferencia de que **Juego]actualiza la terminología usada en los informes por términos de este campo.[!UICONTROL ** For example, users is changed to players. Los informes específicos de juegos se muestran automáticamente en las aplicaciones de juegos.
   * **[!UICONTROL Descripción]**

      (**Optional**) Type a description for the app.



1. Click **[!UICONTROL Save]** to add the new app.

   Después de agregar la aplicación, puede consultar la página Información de la aplicación para ver cómo configurar otras opciones. For more information, see [Manage App Settings](/help/using/c-manage-app-settings/c-manage-app-settings.md).
