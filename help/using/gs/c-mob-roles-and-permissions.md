---
description: En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.
title: Roles y permisos
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: f6a62a46a90c30edaf999085873bf21f2a03a68e
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 48%

---

# Roles y permisos{#roles-and-permissions}

En Adobe Analytics, puede administrar los roles en la página principal de las herramientas de administración.

## Información general {#section_91B8192891E14E5285718C8118912500}

Los roles siguientes administran los permisos en la interfaz de usuario de Mobile Services:

### Administrador de Analytics

Un administrador de Analytics administra grupos de usuarios y asigna permisos, uno de los cuales es el de los administradores de aplicaciones móviles. El administrador del Experience Cloud vincula su Adobe ID con su cuenta de Adobe Analytics, lo que le permite iniciar sesión en la interfaz de usuario de Mobile Services con su Adobe ID. Para obtener más información sobre el administrador del Experience Cloud, consulte [Administración de usuarios y productos de Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) en la guía Componentes de la interfaz central del Experience Cloud.

>[!TIP]
>
>Un administrador existente de Analytics tiene la capacidad de asignar el rol de administrador de Analytics a cualquier usuario.

Para obtener más información sobre esta función, consulte el siguiente contenido en la documentación de Adobe Analytics:

* [Información general sobre la administración de usuarios](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=es)
* [Cambios en los permisos de usuarios y grupos](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Administrador de aplicaciones móviles

Este rol es el administrador de la interfaz de usuario de Mobile Services.

>[!IMPORTANT]
>
>En algunas funciones, como la mensajería push, el administrador de Analytics debe seleccionar la casilla de verificación **[!UICONTROL Creación de segmentos]** en Administración de usuarios.

## Administración del acceso {#section_E6939C2695AA4A0DBF432D50B2670920}

A continuación, presentamos información adicional sobre el acceso a las opciones en la interfaz de usuario de Mobile Services:

### Aplicaciones y grupos de informes

Todas las aplicaciones de Mobile Services están vinculadas a los grupos de informes. Si los usuarios no tienen acceso a un grupo de informes, no tendrán acceso a la aplicación asociada de ese grupo de informes.

### Funciones de Mobile Services y Analytics

Si su empresa no tiene un contrato de Analytics para acceder a alguna función de la interfaz de usuario, como la mensajería push, ningún usuario de la empresa tendrá acceso a ella, sea cual sea su nivel de permiso.

## Roles y permisos {#section_20AA029D5B8C413C8659777E79B11620}

Estos son los roles de la interfaz de usuario de Mobile Services y sus respectivos permisos:

### Administrador de Analytics permissions

* Todos los permisos de administración de usuarios y aplicaciones móviles
* Crear aplicación con un nuevo grupo de informes
* Eliminar aplicación de Mobile Services

   >[!IMPORTANT]
   >
   >Aunque la aplicación se haya eliminado en la interfaz de usuario de Mobile Services, el grupo de informes sigue existiendo en Analytics.

* Administrar configuración de aplicación

   * Habilitar la creación de informes del ciclo vital
   * Habilitar los informes de ubicación
   * Crear/actualizar/eliminar variables y métricas

### Administrador de aplicaciones móviles permissions

* Todos los permisos de usuario
* Crear aplicación con un grupo de informes existente
* Administrar configuración de aplicación

   * Configurar las opciones del SDK de Mobile de la aplicación
   * Configurar los ajustes de la interfaz de usuario de la aplicación
   * Configuración de aplicaciones de App Store vinculadas
   * Configurar las opciones de vínculo universal de la aplicación
   * Configuración de certificados y claves de API de servicios push
   * Crear/actualizar/activar/desactivar/duplicar/archivar/eliminar postbacks
   * Crear/actualizar/archivar/eliminar destinos de vínculo

* Crear/actualizar/archivar vínculos de marketing
* Crear/importar/actualizar/eliminar vínculos de adquisición de elementos heredados
* Crear/importar/actualizar/eliminar configuraciones de lugares (puntos de interés)
* Crear/actualizar/enviar/programar/cancelar/duplicar/archivar/eliminar mensajes push
* Crear/actualizar/activar/desactivar/duplicar/archivar/eliminar mensajes en la aplicación

Para obtener más información sobre grupos y usuarios, consulte el siguiente contenido en la documentación de Adobe Analytics:

* [Configuración de grupos de usuarios (heredado)](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)
* [Agregar un usuario a un grupo](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Usuario de Mobile Services

Esta función solo tiene permisos de visualización y puede proporcionar comentarios en la interfaz de usuario de Mobile Services.

* Proporcionar comentarios en la interfaz de usuario de Mobile Services
* Ver aplicaciones

   >[!IMPORTANT]
   >
   >Los usuarios solo pueden ver los grupos de informes a los que tienen acceso en Adobe Analytics.

* Ver configuración de aplicación

   * Descargar la configuración del SDK de la aplicación
   * Ver toda la configuración de la interfaz de usuario y el SDK
   * Ver la configuración de variables y métricas
   * Ver postbacks
   * Ver destinos de vínculo

* Ver y ejecutar informes
* Ver vínculos de marketing
* Ver y exportar vínculos de adquisición de elementos heredados
* Ver y exportar configuraciones de lugares (puntos de interés)
* Ver mensajes push
* Ver mensajes en la aplicación
