---
description: A partir de iOS 10, Apple le permite crear una extensión denominada extensión independiente que se puede distribuir sin una aplicación contenedora. Con esta extensión, no necesita un grupo de aplicaciones, ya que no hay ninguna aplicación contenedora con la que compartir datos.
solution: Experience Cloud,Analytics
title: Implementación de extensiones independientes
topic-fix: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
exl-id: b51247b6-c4ba-4a00-9ba0-1824450ac067
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 100%

---

# Implementación de extensiones independientes {#stand-alone-extension-implementation}

A partir de iOS 10, Apple le permite crear una extensión denominada extensión independiente que se puede distribuir sin una aplicación contenedora. Con esta extensión, no necesita un grupo de aplicaciones, ya que no hay ninguna aplicación contenedora con la que compartir datos.

>[!IMPORTANT]
>
>Para utilizar extensiones independientes, debe tener la versión 4.13.0 o posterior del SDK de Mobile.

## Configurar la extensión independiente para su uso con el SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

Para configurar su extensión independiente:

1. Compruebe que el archivo `ADBMobileConfig.json` pertenece al destino de la extensión.
1. Vincule las siguientes bibliotecas y marcos:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. En el controlador de vista principal de la extensión, establezca el tipo de extensión en `ADBMobileAppExtensionTypeStandAlone` en el SDK antes de completar cualquier actividad relacionada con el SDK.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Confirme que la aplicación se compila sin errores inesperados.

## Notas adicionales {#section_1C9A55E2309A44BF842310F735702B3D}

Alguna información adicional:

* Se ha agregado un valor de contexto adicional, `a.RunMode`, para indicar si los datos proceden de la aplicación contenedora o de la extensión:

   * `a.RunMode = Application`

      Este valor significa que la visita procede de la aplicación contendora.
   * `a.RunMode = Extension`

      Este valor significa que la visita procede de la extensión.

* En las aplicaciones de extensión de iOS no se activa ninguna llamada de ciclo vital.
