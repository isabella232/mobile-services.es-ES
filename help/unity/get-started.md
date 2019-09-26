---
description: Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.
keywords: Unity
seo-description: Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.
seo-title: Complemento Unity para los SDK de iOS y Android 4.x
solution: Marketing Cloud,Desarrollador
title: Complemento Unity para los SDK de iOS y Android 4.x
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Complemento Unity para los SDK de iOS y Android 4.x {#unity-plug-in-for-the-ios-and-android-x-sdks}

Este complemento le permite enviar llamadas Adobe Analytics desde sus aplicaciones Unity.

Última actualización: **20 de octubre de 2016**

## Primeros pasos {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Descargue el archivo [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) desde GitHub o Developer Connection.

A continuación se muestra el contenido del `ADBMobile.unitypackage` archivo:

* Recursos (raíz)

   * ADBMobile

      * Demostración

         * ADBMobileDemo.cs
         * BooDemo.boo
         * BooScene.unity
         * CSharpScene.unity
         * JavaScriptDemo.js
         * JavaScriptScene.unity
         * SecondScene.unity
         * SecondSceneScript.cs
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

## Importar el complemento ADBMobile a un proyecto Unity {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Abra el proyecto Unity.
1. Haga doble clic en **[!UICONTROL ADBMobile.unitypackage]**.
1. Elija las carpetas que desee importar.

