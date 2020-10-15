---
description: Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.
keywords: Unity
seo-description: Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.
seo-title: Complemento Unity para los SDK de iOS y Android 4.x
solution: Experience Cloud
title: Complemento Unity para los SDK de iOS y Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '141'
ht-degree: 100%

---


# Complemento Unity para los SDK de iOS y Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.

Última actualización: **10 de marzo de 2020**
* [Unity-v4.19.0](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases/tag/v4.19.0-Unity)

## Primeros pasos {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Descargue el archivo ADBMobile.unitypackage de GitHub.

A continuación verá el contenido del archivo `ADBMobile.unitypackage`:

* Recursos (raíz)

   * ADBMobile

   * Complementos

      * ADBMobile.cs
      * Android

         * adobeMobileLibrary-{version}.jar
         * AndroidManifest.xml
         * activos

            * ADBMobileConfig.json
      * iOS

         * ADBMobile.h
         * ADBMobileConfig.json
         * ADBMobileWrapper.h
         * ADBMobileWrapper.mm
         * AdobeMobileLibrary.a


**Carpetas opcionales**: la carpeta *Demo* contiene escenas de Unity y muestras del código.

## Importar el complemento ADBMobile a un proyecto Unity  {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Abra el proyecto Unity.
1. Haga doble clic en **[!UICONTROL ADBMobile.unitypackage]**.
1. Elija las carpetas que desee importar.
