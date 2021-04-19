---
description: Estas extensiones le proporcionan una forma mucho más sencilla de agregar la referencia del SDK para Windows de soluciones de Experience Cloud 4.x en su proyecto.
seo-description: Estas extensiones le proporcionan una forma mucho más sencilla de agregar la referencia del SDK para Windows de soluciones de Experience Cloud 4.x en su proyecto.
seo-title: Extensiones de Windows Visual Studio para soluciones de SDK de Experience Cloud 4.x
solution: Experience Cloud,Analytics
title: Extensiones de Windows Visual Studio para soluciones de SDK de Experience Cloud 4.x
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 16%

---

# Extensiones de Windows Visual Studio para soluciones de SDK de Experience Cloud 4.x {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Esta extensión proporciona una forma mucho más sencilla de agregar la referencia del SDK para Windows de soluciones de Experience Cloud 4.x a su proyecto.

## Instale la biblioteca desde GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Descargue el SDK universal de Windows desde [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Descomprima el archivo descargado localmente.
1. Haga doble clic en el archivo **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** para abrir el instalador.
1. Seleccione **[!UICONTROL Ubicación global]** e instale la biblioteca.

## Agregar referencias al proyecto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Abra el proyecto de Windows 10.
1. Abra el cuadro de diálogo Administrador de referencias.

   ![](assets/ref_manager.png)

1. En la pestaña **[!UICONTROL Extensions]**, busque y seleccione **[!UICONTROL Adobe Mobile SDK]**.
1. Haga clic en **[!UICONTROL OK]** para guardarlo.

   El SDK de Adobe Mobile se agregará al proyecto. Si el paquete **[!UICONTROL Microsoft Visual C++ Runtime]** aún no se ha agregado, este paquete también se agregará al proyecto.

1. En el Administrador de configuración, seleccione un tipo de plataforma y comience a probar la aplicación.
