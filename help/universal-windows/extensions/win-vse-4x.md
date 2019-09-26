---
description: Estas extensiones le proporcionan un modo mucho más sencillo de añadir a su proyecto la referencia del SDK 4.x de Windows para Soluciones de Experience Cloud.
seo-description: Estas extensiones le proporcionan un modo mucho más sencillo de añadir a su proyecto la referencia del SDK 4.x de Windows para Soluciones de Experience Cloud.
seo-title: Extensiones de Windows Visual Studio para el SDK de soluciones de Experience Cloud 4.x
solution: Marketing Cloud,Analytics
title: Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK
topic: Desarrollador e implementación
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Esta extensión proporciona una forma mucho más sencilla de añadir la referencia del SDK de Windows de soluciones de Experience Cloud 4.x en su proyecto.

## Instalar la biblioteca desde GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Descargue el SDK Windows Universal desde [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Descomprima de forma local el archivo descargado.
1. Haga doble clic en el archivo **[!UICONTRTOL ADBMobileUniversalWindowsVSIX.vsix]** para abrir el instalador.
1. Seleccione Ubicación **** global e instale la biblioteca.

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Abra el proyecto de Windows 10.
1. Abra el cuadro de diálogo Administrador de referencias.

   ![](assets/ref_manager.png)

1. En la ficha **[!UICONTROL Extensiones]** , busque y seleccione **[UICONTROL Adobe Mobile SDK]**.
1. Haga clic en **[!UICONTROL Aceptar]para guardarlo.**

   El SDK de Adobe Mobile se agregará a su proyecto. Si aún no se ha agregado el paquete **[UICONTROL Microsoft Visual C++ Runtime]** , este paquete también se agregará al proyecto.

1. En el Administrador de configuración, seleccione un tipo de plataforma y comience a probar la aplicación.

