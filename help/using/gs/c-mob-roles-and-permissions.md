---
description: En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.
seo-description: En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.
seo-title: Roles y permisos
title: Roles y permisos
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 59%

---


# Roles y permisos{#roles-and-permissions}

En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.

## Información general {#section_91B8192891E14E5285718C8118912500}

Los roles siguientes administran los permisos en la interfaz de usuario de Mobile Services:

### Administrador de Analytics

Un administrador de Analytics administra grupos de usuarios y asigna permisos, uno de los cuales es el de los administradores de aplicaciones móviles. El administrador de Experience Cloud vincula su Adobe ID con su cuenta de Adobe Analytics, lo que le permite iniciar sesión en la interfaz de usuario de Mobile Services con su Adobe ID. Para obtener información sobre el administrador de Experience Cloud, consulte [Administración: Administración de usuarios y preguntas más frecuentes](https://docs.adobe.com/content/help/es-ES/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Un administrador existente de Analytics tiene la capacidad de asignar el rol de administrador de Analytics a cualquier usuario.

Para obtener más información sobre este rol, consulte los siguientes temas:

* [Información general sobre la administración de usuarios](https://docs.adobe.com/content/help/es-ES/analytics/admin/user-product-management/user-management/users.html)

* [Cambios en los permisos de usuarios y grupos](https://docs.adobe.com/content/help/es-ES/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Administrador de aplicaciones móviles

Este rol es el administrador de la interfaz de usuario de Mobile Services.

>[!IMPORTANT]
>
>En algunas funciones, como la mensajería push, el administrador de Analytics debe seleccionar la casilla de verificación **[!UICONTROL Creación de segmentos]** en Administración de usuarios.

## Administración del acceso {#section_E6939C2695AA4A0DBF432D50B2670920}

A continuación, presentamos información adicional sobre el acceso a las opciones en la interfaz de usuario de Mobile Services:

### Aplicaciones y grupos de informes

Todas las aplicaciones de Mobile Service están vinculadas a grupos de informes. Si los usuarios no tienen acceso a un grupo de informes, no tendrán acceso a la aplicación asociada de ese grupo de informes.

### Funciones de Mobile Services y Analytics

Si su empresa no tiene un contrato de Analytics para acceder a alguna función de la interfaz de usuario, como la mensajería push, ningún usuario de la empresa tendrá acceso a ella, sea cual sea su nivel de permiso.

## Roles y permisos {#section_20AA029D5B8C413C8659777E79B11620}

Estos son los roles de la interfaz de usuario de Mobile Services y sus respectivos permisos:

### Administrador de Analytics

* Todos los permisos de administración de usuarios y aplicaciones móviles
* Crear aplicación con nuevo grupo de informes
* Eliminar aplicación de Mobile Services

   >[!IMPORTANT]
   >
   >Aunque la aplicación se haya eliminado en la interfaz de usuario de Mobile Services, el grupo de informes sigue existiendo en Analytics.

* Administrar configuración de aplicación

   * Habilitar Sistema de informes del ciclo vital
   * Habilitar Sistema de informes de ubicación
   * Crear/actualizar/eliminar variables y métricas

### Administrador de aplicaciones móviles

* Todos los permisos de usuario
* Crear aplicación con grupo de informes existente
* Administrar configuración de aplicación

   * Configuración de las opciones del SDK para móviles de la aplicación
   * Configurar la configuración de la interfaz de usuario de la aplicación
   * Configuración de aplicaciones de App Store vinculadas
   * Configurar las opciones de vínculo universal de la aplicación
   * Configuración de certificados y claves de API de servicios push
   * Crear/actualizar/activar/desactivar/Duplicado/archivar/eliminar postbacks
   * Crear/actualizar/archivar/eliminar destinos de vínculo

* Crear/actualizar/archivar vínculos de marketing
* Crear/importar/actualizar/eliminar vínculos de adquisición preexistentes
* Crear/importar/actualizar/eliminar configuraciones de lugares (puntos de interés)
* Crear/actualizar/enviar/programar/cancelar/Duplicado/archivar/eliminar mensajes push
* Crear/actualizar/activar/desactivar/Duplicado/archivar/eliminar mensajes en la aplicación

Para obtener más información sobre grupos y usuarios, consulte:

* [Configuración de grupos de usuarios](https://docs.adobe.com/content/help/es-ES/analytics/admin/user-product-management/user-groups/groups.html)
* [Agregar un usuario a un grupo](https://docs.adobe.com/content/help/es-ES/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Usuario de Mobile Services

Esta función solo tiene permisos de vista y puede proporcionar comentarios en la interfaz de usuario de Mobile Services.

* Proporcionar comentarios en la interfaz de usuario de Mobile Services
* Aplicaciones de vista

   >[!IMPORTANT]
   >
   >Los usuarios solo pueden ver los grupos de informes a los que tienen acceso en Adobe Analytics.

* Configuración de la aplicación de vista

   * Descargar configuración del SDK de la aplicación
   * Vista de toda la configuración de la interfaz de usuario y del SDK
   * Configuración de variables y métricas de vista
   * Postbacks de vista
   * Destinos del vínculo de vista

* Ver y ejecutar informes
* Ver vínculos de marketing
* Vista y exportación de vínculos de adquisición heredados
* Vista y configuración de lugares de exportación (puntos de interés)
* Mensajes push de vista
* Vista de mensajes en la aplicación
