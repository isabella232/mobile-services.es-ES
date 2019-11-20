---
description: Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.
keywords: Unity
seo-description: Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.
seo-title: Complemento Unity para los SDK de iOS y Android 4.x
solution: Experience Cloud,Desarrollador
title: Complemento Unity para los SDK de iOS y Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: df4ff7128357a18c56d840eb5697f9c8813ad751

---


# Complemento Unity para los SDK de iOS y Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.

Última actualización: **12 de noviembre de 2019**

## Primeros pasos {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Descargue el archivo [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) desde GitHub o Developer Connection.

A continuación se muestra el contenido del archivo `ADBMobile.unitypackage`:

* Recursos (raíz)

   * ADBMobile

   * Complementos

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * Recursos

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


Carpetas opcionales: la carpeta Demostración contiene escenas de Unity y código de muestra para cada uno de los lenguajes de secuencia de comandos compatibles.

## Importar el complemento ADBMobile a un proyecto Unity  {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Abra el proyecto Unity.
1. Haga doble clic en **[!UICONTROL ADBMobile.unitypackage]**.
1. Elija las carpetas que desee importar.

