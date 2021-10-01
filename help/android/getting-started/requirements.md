---
description: 'Antes de configurar un grupo de informes y recopilar datos de aplicaciones Android, complete las siguientes tareas previas necesarias '
solution: Experience Cloud,Analytics
title: Antes de comenzar
topic-fix: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
exl-id: e9c0fd94-b61d-4f56-97b8-f71aac096c93
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 95%

---

# Antes de comenzar {#before-you-start}

Antes de configurar un grupo de informes y recopilar datos de aplicaciones Android, complete las siguientes tareas previas necesarias:

## Tareas específicas de funciones {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Los administradores de Analytics y los desarrolladores de aplicaciones deben completar las siguientes tareas:

### Administradores de Analytics

Para configurar un grupo de informes y recopilar datos de aplicaciones móviles:

1. Complete una de las secciones de [Inicio de sesión en la interfaz de usuario de Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Cree una cuenta de Analytics para cada desarrollador de aplicaciones.

Los desarrolladores de aplicaciones ahora tienen acceso a la vista de los grupos de informes que ha creado.

>[!IMPORTANT]
>
>Para crear un nuevo grupo de informes y descargar los SDK, debe ser administrador de Analytics.

### Desarrolladores de aplicaciones

1. Asegúrese de que su administrador de Analytics haya completado los pasos detallados en la sección *Administradores de Analytics* en [Tareas específicas de roles](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC).
1. Verifique que su administrador de Analytics haya completado una de las secciones de [Inicio de sesión en la interfaz de usuario de Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8).
1. Cuando se haya configurado el grupo de informes, complete los pasos detallados en [Descargar el SDK](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46).

Para obtener más información sobre los roles y los permisos, consulte [Roles y permisos](/help/using/gs/c-mob-roles-and-permissions.md).

## Inicio de sesión en la interfaz de usuario de Adobe Mobile Services   {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services es la interfaz de sistema de informes principal para el análisis y la segmentación de aplicaciones móviles. Después de completar estos pasos, puede descargar un archivo de configuración preconfigurado con el servidor de recopilación de datos, el grupo de informes y muchos otros ajustes.

Puede iniciar sesión en la interfaz de usuario de Adobe Mobile Services de una de las siguientes maneras:

### Experience Cloud

Inicie sesión en [Experience Cloud](https://experiencecloud.adobe.com) con su Adobe ID. Este método asume que su empresa está aprovisionada en Experience Cloud y que usted ha vinculado su cuenta de Analytics. Para obtener más información, consulte [Administrar usuarios y productos del Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) en la guía Componentes de la interfaz central del Experience Cloud.

>[!TIP]
>
>Si no está seguro de si su empresa está aprovisionada en Experience Cloud, utilice su cuenta existente de Adobe Analytics.

### Adobe Analytics

Haga clic en **[!UICONTROL Iniciar sesión en Analytics]** e introduzca su nombre de empresa de Analytics, el nombre de usuario y la contraseña.

## Crear un grupo de informes {#section_7BC602ED1ABA42C6AB722F506B5219F3}

Para crear un grupo de informes a fin de recopilar datos de aplicaciones y definir una aplicación:

1. Inicie sesión en [Adobe Mobile Services](https://mobilemarketing.adobe.com).
1. Haga clic en **[!UICONTROL Crear una aplicación]**.

   Si no ve este botón, haga clic en **[!UICONTROL Administrar aplicaciones]** > **[!UICONTROL Agregar]**.

1. En la lista desplegable **[!UICONTROL Grupo de informes]**, seleccione **[!UICONTROL Nuevo grupo de informes]**.

1. Introduzca el nombre de su aplicación y seleccione un tipo de grupo de informes.

   Un ejemplo de ID de grupo de informes es `mycomobileappdev`. Es necesario que establezca grupos de informes y aplicaciones separados para las versiones de desarrollo y de producción, de modo que pueda repetir estos pasos cuando esté preparado para configurar la versión de producción.
1. En **[!UICONTROL ID del grupo de informes]**, compruebe que se muestra el nombre del grupo de informes.
1. En **[!UICONTROL Copiar la configuración de]**, verifique que la opción **[!UICONTROL Plantilla de aplicación móvil]** esté seleccionada.

   Esta plantilla permite que las marcas de fecha y hora recopilen datos sin conexión y activar las variables de soluciones móviles para capturar métricas del ciclo vital.

1. Seleccione su zona horaria y su moneda, y haga clic en **[!UICONTROL Guardar]**.

## Descargar el SDK {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Para descargar el SDK de Mobile:

1. Para iniciar sesión en la interfaz de usuario de Mobile Services, ingrese [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) en un navegador.
1. En el panel izquierdo, haga clic en la lista desplegable **[!UICONTROL Todas las aplicaciones]** y seleccione la aplicación.
También puede seleccionarla en el panel derecho.

   >[!IMPORTANT]
   >
   >Para ver su aplicación en el panel derecho, primero debe crearla. Para obtener información sobre cómo crear una aplicación, consulte [Agregar una aplicación nueva](/help/using/manage-apps/t-new-app.md).

1. En la aplicación, en el panel izquierdo, haga clic en **[!UICONTROL Administrar configuración de la aplicación]**.

   >[!IMPORTANT]
   >
   >Si no ve la opción **[!UICONTROL Administrar configuración de la aplicación]**, asegúrese de haber iniciado sesión en Adobe Mobile Services. Para verificarlo, haga clic en el icono del ![conmutador de soluciones](assets/solution-switcher.png) en la parte superior derecha de la página y asegúrese de que **[!UICONTROL Adobe Mobile Services]** se visualice en la parte superior izquierda.

1. En la parte inferior de la página Administrar configuración de la aplicación, en la sección **[!UICONTROL Descargas del SDK de la aplicación]**, descargue el SDK y la aplicación de ejemplo para su plataforma.

>[!TIP]
>
>La descarga del SDK incluye automáticamente un archivo de configuración para su aplicación, por lo que no es necesario que descargue ese archivo separadamente. Sin embargo, si ya ha descargado el SDK y quiere actualizar la configuración, descargue de nuevo el archivo de configuración.

Si utiliza Android Studio, también puede añadir lo siguiente al archivo `build.gradle` de su aplicación:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

Recuerde la información siguiente:

* Reemplace el número de versión del ejemplo de código con la versión adecuada de los SDK de Android.
* Descargue el archivo de configuración e inclúyalo en su proyecto.
