---
description: En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.
title: Roles y permisos
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7b26c852dd9dba67a8b5e3228c1fecadfb465dca
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 49%

---

# Roles y permisos{#roles-and-permissions}

En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.

## Información general {#section_91B8192891E14E5285718C8118912500}

Los roles siguientes administran los permisos en la interfaz de usuario de Mobile Services:

### Administrador de Analytics

Un administrador de Analytics administra grupos de usuarios y asigna permisos, uno de los cuales es el de los administradores de aplicaciones móviles. The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. [](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=es)

>[!TIP]
>
>Un administrador existente de Analytics tiene la capacidad de asignar el rol de administrador de Analytics a cualquier usuario.

### Administrador de aplicaciones móviles

Este rol es el administrador de la interfaz de usuario de Mobile Services.

>[!IMPORTANT]
>
>En algunas funciones, como la mensajería push, el administrador de Analytics debe seleccionar la casilla de verificación **[!UICONTROL Creación de segmentos]** en Administración de usuarios.

## Administración del acceso {#section_E6939C2695AA4A0DBF432D50B2670920}

A continuación, presentamos información adicional sobre el acceso a las opciones en la interfaz de usuario de Mobile Services:

### Aplicaciones y grupos de informes

All Mobile Service apps are tied to report suites. If users do not have access to a report suite, they will not have access to that report suite&#39;s associated app.

### Funciones de Mobile Services y Analytics

Si su empresa no tiene un contrato de Analytics para acceder a alguna función de la interfaz de usuario, como la mensajería push, ningún usuario de la empresa tendrá acceso a ella, sea cual sea su nivel de permiso.

## Roles y permisos {#section_20AA029D5B8C413C8659777E79B11620}

Estos son los roles de la interfaz de usuario de Mobile Services y sus respectivos permisos:

### Administrador de Analytics permissions

* Todos los permisos de administración de usuarios y aplicaciones móviles
* Create App with new report suite
* Delete App from Mobile Services

   >[!IMPORTANT]
   >
   >Aunque la aplicación se haya eliminado en la interfaz de usuario de Mobile Services, el grupo de informes sigue existiendo en Analytics.

* Administrar configuración de aplicación

   * Enable Lifecycle Reporting
   * Enable Location Reporting
   * Create/Update/Delete Variables and Metrics

### Administrador de aplicaciones móviles permissions

* All User Permissions
* Create App with existing report suite
* Administrar configuración de aplicación

   * Configure App&#39;s Mobile SDK options
   * Configure App&#39;s UI settings
   * Configure linked App Store apps
   * Configure App&#39;s Universal Link options
   * Configure Push Services certs and API keys
   * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
   * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Create/Import/Update/Delete Legacy Acquisition Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see the following content in the Adobe Analytics documentation:

* [](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=es)
* [Agregar un usuario a un grupo](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Usuario de Mobile Services

This role has view-only permissions and can provide feedback in the Mobile Services UI.

* Provide Feedback on Mobile Services UI
* View Apps

   >[!IMPORTANT]
   >
   >Los usuarios solo pueden ver los grupos de informes a los que tienen acceso en Adobe Analytics.

* View App Settings

   * Download App SDK configuration
   * View all UI and SDK settings
   * View Variables and Metrics configuration
   * View Postbacks
   * View Link Destinations

* Ver y ejecutar informes
* Ver vínculos de marketing
* View and Export Legacy Acquisition Links
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages
