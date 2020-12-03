---
description: Complete estos pasos para configurar un grupo de informes con los que recopilar datos de aplicaciones iOS.
seo-description: Complete estos pasos para configurar un grupo de informes con los que recopilar datos de aplicaciones iOS.
seo-title: Antes de comenzar
solution: Experience Cloud,Analytics
title: Antes de comenzar
topic: Developer and implementation
uuid: 04133f68-3618-41fd-8a13-aec5b6f04df6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 100%

---


# Antes de comenzar {#before-you-start}

Complete estos pasos para configurar un grupo de informes con los que recopilar datos de aplicaciones iOS.

## Tareas específicas de funciones {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Los administradores de Analytics y los desarrolladores de aplicaciones deben completar las siguientes tareas:

### Administradores de Analytics

Para configurar un grupo de informes y recopilar datos de aplicaciones móviles:

1. Complete una de las secciones de [Inicio de sesión en la interfaz de usuario de Adobe Mobile Services](/help/ios/getting-started/getting-started.md).
1. Cree una cuenta de Analytics para cada desarrollador de aplicaciones.

Los desarrolladores de aplicaciones ahora tienen acceso a la vista de los grupos de informes que ha creado.

>[!IMPORTANT]
>
>Para crear un nuevo grupo de informes y descargar los SDK, debe ser administrador de Analytics.

### Desarrolladores de aplicaciones

1. Compruebe que su administrador de Analytics haya completado los pasos de la sección *Administradores de Analytics* en la sección anterior.

1. Verifique que su administrador de Analytics haya completado una de las secciones de *Inicio de sesión en la interfaz de usuario de Adobe Mobile Services*.
1. Cuando se haya configurado el grupo de informes, complete los pasos de la sección *Descargar el SDK*.

Para obtener más información sobre los roles y los permisos, consulte [Roles y permisos](/help/using/gs/c-mob-roles-and-permissions.md).

## Inicio de sesión en la interfaz de usuario de Adobe Mobile Services   {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services es la interfaz de sistema de informes principal para el análisis y la segmentación de aplicaciones móviles. Después de completar estos pasos, puede descargar un archivo de configuración preconfigurado con el servidor de recopilación de datos, el grupo de informes y muchos otros ajustes.

Puede iniciar sesión en la interfaz de usuario de Adobe Mobile Services de una de las siguientes maneras:

* **Experience Cloud**

   Inicie sesión en [Experience Cloud](https://marketing.adobe.com) con su Adobe ID.

   Este método supone que su empresa ha sido aprovisionada y que ha vinculado su cuenta de Analytics. Para obtener más información sobre el aprovisionamiento, consulte [Administrar usuarios y productos de Experience Cloud](https://docs.adobe.com/content/help/es-ES/core-services/interface/manage-users-and-products/admin-getting-started.html). Para obtener más información sobre cómo vincular su cuenta, consulte [Organizaciones y vinculación de cuentas](https://docs.adobe.com/content/help/es-ES/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >Si no está seguro de si su empresa está aprovisionada en Experience Cloud, utilice su cuenta existente de Adobe Analytics.

* **Adobe Analytics**

   Haga clic en **[!UICONTROL Iniciar sesión en Analytics]** e introduzca su nombre de empresa de Analytics, el nombre de usuario y la contraseña.

## Crear un grupo de informes {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Para crear un grupo de informes a fin de recopilar datos de aplicaciones y definir una aplicación:

1. Haga clic en **[!UICONTROL Crear una aplicación nueva]**.

   Si no ve este botón, haga clic en **[!UICONTROL Administrar aplicaciones]** > **[!UICONTROL Agregar]**.

1. En la lista desplegable **[!UICONTROL Grupo de informes]**, seleccione **[!UICONTROL Nuevo grupo de informes]**.

1. Introduzca el nombre de su aplicación y seleccione un ID de grupo de informes exclusivo.

   Un ejemplo de ID de grupo de informes es `mycomobileappdev`. Debe configurar grupos de informes y aplicaciones independientes para las versiones de desarrollo y producción. Cuando esté listo para configurar la versión de producción, repita estos pasos.
1. Deje seleccionado **[!UICONTROL Plantilla de aplicación móvil]**.

   Esta plantilla permite que las marcas de fecha y hora recopilen datos sin conexión y activar las variables de soluciones móviles para capturar métricas del ciclo vital.

1. Seleccione su **[!UICONTROL Zona horaria]** y su **[!UICONTROL Moneda]** y haga clic en **[!UICONTROL Guardar]**.

## Descargar el SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Para descargar el SDK de Mobile:

1. Inicie sesión en Mobile Services y abra su aplicación de una de las formas siguientes:

   * En la lista desplegable **[!UICONTROL Todas las aplicaciones]**, seleccione su aplicación.
   * En el panel derecho, busque su aplicación y ábrala.

1. Haga clic en **[!UICONTROL Administrar configuración de aplicación]**.
1. En la sección **[!UICONTROL Descargas del SDK de la aplicación]**, desplácese hasta la sección **[!UICONTROL Descargas del SDK de la aplicación]**.

1. Descargue el SDK y la aplicación de ejemplo para su plataforma.

>[!TIP]
>
>La descarga del SDK incluye automáticamente un archivo de configuración para su aplicación, por lo que no es necesario que descargue ese archivo separadamente. Sin embargo, si ya ha descargado el SDK y quiere actualizar la configuración, descargue de nuevo el archivo de configuración.

