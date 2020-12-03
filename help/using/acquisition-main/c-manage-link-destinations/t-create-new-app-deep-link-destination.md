---
description: Puede crear un nuevo destino de vínculo que dirija a los usuarios a un vínculo web o profundo en su aplicación.
keywords: mobile
seo-description: Puede crear un nuevo destino de vínculo que dirija a los usuarios a un vínculo web o profundo en su aplicación.
seo-title: Crear un nuevo destino de vínculo
solution: Experience Cloud,Analytics
title: Crear un nuevo destino de vínculo
topic: Metrics
uuid: 390e3dea-0221-4f97-980d-a90ca9f162fa
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---


# Crear un nuevo destino de vínculo {#create-new-link-destination}

Puede crear un nuevo destino de vínculo que dirija a los usuarios a un vínculo web o profundo en su aplicación.

1. En la interfaz de usuario de Mobile Services, haga clic en **[!UICONTROL Administrar aplicaciones]**.
1. Haga clic en el nombre de la aplicación para mostrar la página Información de la aplicación.
1. Haga clic en **[!UICONTROL Administrar destinos de enlace]**.
1. Haga clic en **[!UICONTROL Crear nuevo]**.
1. Rellene los campos siguientes:
   * **[!UICONTROL Título]**

      Escriba un nombre descriptivo para el destino de vínculo de la aplicación. El título solo aparece en la página Administrar destinos de vínculo de la interfaz de usuario de Adobe Mobile Services. Un nombre descriptivo le ayuda a usted y a otras personas de su organización a encontrar rápidamente destinos de vínculo específicos y puede proporcionar información sobre su finalidad.

   * **[!UICONTROL Tipo de vínculo]**

      Esta es una lista de los tipos de vínculos disponibles:

      * **[!UICONTROL Vínculo profundo de la aplicación]**

         Proporcione un vínculo profundo de esquema de URI (por ejemplo, `yourapp://section`). Los destinos de vínculo profundo de la aplicación son vínculos profundos de esquema de URI que dirigen a los usuarios a un vínculo profundo de su aplicación. Por ejemplo, puede dirigir a los usuarios a una línea de productos específica en la aplicación móvil de un comerciante en línea.

      * **[!UICONTROL Vínculo web]**

         Escriba una URL web HTTP o HTTPS, por ejemplo,`https://adobe.com`. Los destinos de vínculo web dirigen a los usuarios a una dirección URL. Por ejemplo, puede dirigir a los usuarios a una línea de productos en el sitio web de un comerciante en línea.

      * **[!UICONTROL Vínculo híbrido]**

         Escriba un vínculo universal de iOS o un vínculo de aplicación de Android (por ejemplo, `https://yourwebsite.com`). Los vínculos híbridos admiten vínculos universales iOS o vínculos para aplicaciones Android.
   * **[!UICONTROL Aplicación]** Seleccione la aplicación asociada al vínculo que va a proporcionar.

      >[!TIP]
      >
      >Esta información solo es obligatoria si ha seleccionado un vínculo híbrido o un vínculo profundo de aplicación en **[!UICONTROL Tipo de vínculo]**. Si la aplicación no aparece en la lista de selección, haga clic en **[!UICONTROL Agregar nueva aplicación]** para hacer referencia a una nueva aplicación de una tienda de aplicaciones.

   * **[!UICONTROL Tipo de vínculo]**

      Escriba la dirección URL real del vínculo seleccionado. La etiqueta de este campo variará según el tipo de vínculo seleccionado.

   * **[!UICONTROL Notas]**

      Escriba notas opcionales para el destino. Las notas adicionales solo aparecen en la página Administrar destinos de vínculo de la interfaz de usuario de Adobe Mobile Services. Las notas adicionales pueden ayudarles a usted y otros usuarios de su organización a encontrar rápidamente un destino de vínculo concreto, así como proporcionar información sobre su finalidad, la campaña a la que se vincula o cualquier otra información que considere importante.


1. Haga clic en **Guardar**.
