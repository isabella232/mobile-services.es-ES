---
description: Complete estos pasos para configurar un grupo de informes con los que recopilar datos de aplicaciones iOS.
seo-description: Complete estos pasos para configurar un grupo de informes con los que recopilar datos de aplicaciones iOS.
seo-title: Antes de comenzar
solution: Marketing Cloud, Analytics
title: Antes de comenzar
topic: Desarrollador e implementación
uuid: 04133 f 68-3618-41 fd -8 a 13-aec 5 b 6 f 04 df 6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

Complete estos pasos para configurar un grupo de informes con los que recopilar datos de aplicaciones iOS.

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Los administradores de Analytics y los desarrolladores de aplicaciones deben completar las siguientes tareas:

### Administradores de Analytics

Para configurar un grupo de informes y recopilar datos de aplicaciones móviles:

1. Se ha completado una de las secciones de [Inicio de sesión en la interfaz de usuario de Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Cree una cuenta de Analytics para cada desarrollador de aplicaciones.

Ahora, los desarrolladores de aplicaciones tienen acceso para ver los grupos de informes que usted crea.

>[!IMPORTANT]
>
>Para crear un nuevo grupo de informes y descargar los SDK, debe ser administrador de Analytics.

### Desarrolladores de aplicaciones

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

Para obtener más información sobre los roles y los permisos, consulte [Roles y permisos](/help/using/gs/c-mob-roles-and-permissions.md).

## Inicio de sesión en la interfaz de usuario de Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services es la principal interfaz de realización de informes para análisis y segmentación de aplicaciones móviles. Cuando complete estos pasos podrá descargar un archivo de configuración preconfigurado con su servidor de recopilación de datos, su grupo de informes y muchos otros ajustes.

Puede iniciar sesión en Adobe Mobile Services de una de las siguientes formas:

* **Experience Cloud**

   Inicie sesión en [Experience Cloud](https://marketing.adobe.com) con su Adobe ID.

   Este método asume que su empresa se ha aprovisionado y que ha vinculado su cuenta de Analytics. Para obtener más información sobre el aprovisionamiento, consulte [Administración de usuarios y productos de Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html). Para obtener más información sobre cómo vincular su cuenta, consulte [Organizaciones y vinculación de cuentas](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >Si no está seguro de si su empresa ha sido aprovisionada en Experience Cloud, utilice su cuenta existente de Adobe Analytics.

* **Adobe Analytics**

   Haga clic en **[!UICONTROL Iniciar sesión en Analytics]** e introduzca su nombre de empresa de Analytics, el nombre de usuario y la contraseña.

## Crear un grupo de informes {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Para crear un grupo de informes a fin de recopilar datos de aplicaciones y definir una aplicación:

1. Haga clic en **[!UICONTROL Crear una aplicación nueva]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. En la lista desplegable **[!UICONTROL Grupo de informes]**, seleccione **[!UICONTROL Nuevo grupo de informes]**.

1. Introduzca el nombre de su aplicación y seleccione un ID de grupo de informes exclusivo.

   Un ejemplo de ID de grupo de informes es `mycomobileappdev`. Debe configurar grupos de informes y aplicaciones separados para las versiones de desarrollo y producción. Cuando esté listo para configurar la versión de producción, repita estos pasos.
1. Deje seleccionado **[!UICONTROL Plantilla de aplicación móvil].**

   Esta plantilla permite que las marcas de fecha y hora recopilen datos sin conexión y activar las variables de soluciones móviles para capturar métricas del ciclo vital.

1. Select your **[!UICONTROL Timezone]**, your **[!UICONTROL Currency]**, and click **[!UICONTROL Save]**.

## Descargar el SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Para descargar el SDK de Mobile:

1. Inicie sesión en Mobile Services y abra la aplicación de una de las siguientes maneras:

   * En la lista desplegable **[!UICONTROL Todas las aplicaciones], seleccione su aplicación.**
   * En el panel derecho, busque su aplicación y ábrala.

1. Haga clic en **[!UICONTROL Administrar configuración de aplicación]**.
1. En la sección **[!UICONTROL Descargas del SDK de la aplicación]**, desplácese hasta la sección **Descargas del SDK de la aplicación[!UICONTROL .]**

1. Descargue el SDK y la aplicación de ejemplo para su plataforma.

>[!TIP]
>
>En la descarga del SDK se incluye automáticamente un archivo de configuración para su aplicación, por lo que no es necesario descargar ese archivo por separado. Sin embargo, si ya ha descargado el SDK y quiere actualizar la configuración, descargue de nuevo el archivo de configuración.

