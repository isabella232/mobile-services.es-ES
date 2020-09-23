---
description: Estas extensiones le proporcionan una forma mucho más sencilla de agregar la referencia del SDK de Windows para Soluciones Experience Cloud 4.x en su proyecto.
seo-description: Estas extensiones le proporcionan una forma mucho más sencilla de agregar la referencia del SDK de Windows para Soluciones Experience Cloud 4.x en su proyecto.
seo-title: Extensiones de Windows Visual Studio para soluciones de SDK de Experience Cloud 4.x
solution: Experience Cloud,Analytics
title: Extensiones de Windows Visual Studio para soluciones de SDK de Experience Cloud 4.x
topic: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 16%

---


# Extensiones de Windows Visual Studio para soluciones de SDK de Experience Cloud 4.x {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Estas extensiones le proporcionan una forma mucho más sencilla de agregar la referencia del SDK de Windows para Soluciones Experience Cloud 4.x en su proyecto.

## Instalación de la biblioteca desde GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Descargue el SDK universal de Windows desde [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Descomprima el archivo descargado localmente.
1. Haga clic con el doble en el archivo ADBMobileWindowsStoreVSIX.vsix o ADBMobileWindowsPhoneVSIX.vsix para abrir el instalador.

1. Seleccione Ubicación **** global e instale la biblioteca.

## Añadir referencias al proyecto {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Abra el proyecto de Windows 8.1 o Windows Phone 8.1.
1. Abra el cuadro de diálogo Administrador de referencias.

   ![](assets/ref_manager.png)

1. En la ficha **[!UICONTROL Extensiones]** de Windows 8.1 o Windows Phone 8.1, busque y seleccione **[!UICONTROL Adobe Mobile SDK]**.
1. Click **[!UICONTROL OK]** to save it.

   El SDK de Adobe Mobile se agregará al proyecto y, si aún no se ha agregado, también se agregará el paquete Tiempo de ejecución **[!UICONTROL de]** Microsoft Visual C++.

1. En el Administrador de configuración, seleccione un tipo de plataforma y comience a probar la aplicación.

