---
description: En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.
seo-description: En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.
seo-title: Roles y permisos
title: Roles y permisos
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# Roles and permissions{#roles-and-permissions}

En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.

## Información general {#section_91B8192891E14E5285718C8118912500}

Los roles siguientes administran los permisos en la interfaz de usuario de Mobile Services:

### Administrador de Analytics

Un administrador de Analytics administra grupos de usuarios y asigna permisos, uno de los cuales es el de los administradores de aplicaciones móviles. El administrador de Experience Cloud vincula su Adobe ID a su cuenta de Adobe Analytics, lo que le permite iniciar sesión en la interfaz de usuario de Mobile Services con su Adobe ID. Para obtener información sobre el administrador de Experience Cloud, consulte [Administración: Administración de usuarios y preguntas más frecuentes](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Un administrador de Analytics existente puede asignar la función de administrador de Analytics a cualquier usuario.

Para obtener más información sobre este rol, consulte los siguientes temas:

* [Información general sobre la administración de usuarios](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/users.html)

* [Cambios en los permisos de usuario y grupo](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Administrador de aplicaciones móviles

Este rol es el administrador de la interfaz de usuario de Mobile Services.

>[!IMPORTANT]
>
>For some features, such as push messaging, the Analytics Admin must select the **[!UICONTROL Segment Creation]** check box in User Management.

## Managing access {#section_E6939C2695AA4A0DBF432D50B2670920}

A continuación, presentamos información adicional sobre el acceso a las opciones en la interfaz de usuario de Mobile Services:

### Aplicaciones y grupos de informes

Todas las aplicaciones de Mobile Service están enlazadas a grupos de informes. Si los usuarios no tienen acceso a un grupo de informes, tampoco tendrán acceso a la aplicación asociada a dicho grupo de informes.

### Funciones de Mobile Services y Analytics

Si su empresa no tiene un contrato de Analytics para acceder a alguna función de la interfaz de usuario, como la mensajería push, ningún usuario de la empresa tendrá acceso a ella, sea cual sea su nivel de permiso.

## Roles and permissions {#section_20AA029D5B8C413C8659777E79B11620}

Estos son los roles de la interfaz de usuario de Mobile Services y sus respectivos permisos:

### Administrador de Analytics

* Todos los permisos de administración de usuarios y aplicaciones móviles
* Crear una aplicación con un grupo de informes nuevo
* Eliminar una aplicación de Mobile Services

   >[!IMPORTANT]
   >
   >Aunque la aplicación se ha eliminado en la interfaz de usuario de Mobile Services, el grupo de informes aún existe en Analytics.

* Administrar configuración de aplicación

   * Activar la creación de informes de ciclo de vida
   * Activar la creación de informes de ubicación
   * Crear/Actualizar/Eliminar variables y métricas

### Administrador de aplicaciones móviles

* Todos los permisos de usuario
* Crear una aplicación con un grupo de informes existente
* Administrar configuración de aplicación

   * Configurar las opciones del SDK de Mobile de la aplicación
   * Configurar los ajustes de la interfaz de usuario de la aplicación
   * Configurar las aplicaciones vinculadas de las tiendas de aplicaciones
   * Configurar las opciones de vínculos universales de la aplicación
   * Configurar los certificados y las claves de API de los servicios push
   * Crear/actualizar/activar/desactivar/duplicar/archivar/eliminar postbacks
   * Crear/actualizar/archivar/eliminar destinos de vínculo

* Crear/actualizar/archivar vínculos de marketing
* Crear/importar/actualizar/eliminar vínculos de adquisiciones preexistentes
* Crear/importar/actualizar/eliminar configuraciones de lugares (puntos de interés)
* Crear/actualizar/enviar/programar/cancelar/duplicar/archivar/eliminar mensajes push
* Crear/actualizar/activar/desactivar/duplicar/archivar/eliminar mensajes en la aplicación

Para obtener más información sobre los grupos y los usuarios, consulte:

* [Configuración de grupos de usuarios](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-groups/groups.html)
* [Agregar un usuario a un grupo](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Usuario de Mobile Services

Este rol solo tiene permiso de visualización y puede proporcionar comentarios en la interfaz de usuario de Mobile Services.

* Proporcionar comentarios en la interfaz de usuario de Mobile Services
* Ver aplicaciones

   >[!IMPORTANT]
   >
   >Users can only see the report suites for which they have access in Adobe Analytics.

* Ver la configuración de la aplicación

   * Descargar la configuración del SDK de la aplicación
   * Ver toda la configuración de la interfaz de usuario y el SDK
   * Ver la configuración de las variables y métricas
   * Ver los postbacks
   * Ver los destinos de los vínculos

* Ver y ejecutar informes
* Ver vínculos de marketing
* Ver y exportar vínculos de adquisiciones preexistentes
* Ver y exportar configuraciones de lugares (puntos de interés)
* Ver mensajes push
* Ver mensajes en la aplicación
