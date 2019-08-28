---
description: Puede dirigir a los usuarios a un destino dependiendo de si tienen la aplicación instalada (un vínculo profundo de la aplicación) o no instalada (a un sitio web o una tienda de aplicaciones).
keywords: móvil
seo-description: Puede dirigir a los usuarios a un destino dependiendo de si tienen la aplicación instalada (un vínculo profundo de la aplicación) o no instalada (a un sitio web o una tienda de aplicaciones).
seo-title: Intersticiales
solution: Marketing Cloud, Analytics
title: Intersticiales
topic: Métricas
uuid: 7 dce 8 ab 2-2 a 5 d -4384-ac 1 e-e 31 dfaa 33654
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Intersticiales{#interstitials}

Puede dirigir a los usuarios a un destino dependiendo de si tienen la aplicación instalada (un vínculo profundo de la aplicación) o no instalada (a un sitio web o una tienda de aplicaciones). Es mejor que sean los usuarios quienes elijan las rutas. Los especialistas en marketing pueden proporcionar elecciones de usuario configurando una página intersticial que muestre a los usuarios los destinos de aterrizaje disponibles.

Para configurar un intersticial al crear un vínculo de marketing:

1. Click **[!UICONTROL Edit Deep Link Interstitial]**.

   ![Intersticial de vínculo profundo](assets/interstitial2.png)

1. Rellene los campos siguientes:

   * **[!UICONTROL HTML personalizada]**

      Seleccione su página HTML intersticial personalizada.

      Al utilizar intersticiales personalizados, los especialistas en marketing pueden personalizar páginas de aterrizaje intersticiales con HTML/CSS/JS personalizado, que le permite personalizar sus páginas.

      Estos son los requisitos de la página HTML:

      * Debe ser un archivo HTML.
      * Must contain the `%%DEST%%` and `%%FALLBACK%%` placeholders.
      * El HTML cargado se suministra en un `<iframe>`.

         Debe asegurarse de que los objetivos del vínculo apunten a una ventana principal. You can include `<base target="_parent" />` in `<head>` or specify a target property for each `<a/>` individually.

         >[!TIP]
         >
         >Si carga HTML personalizado, las otras cuatro opciones de esta tabla no se utilizarán a menos que elimine el archivo cargado.
   * **[!UICONTROL Dirección URL de imagen]**

      Especifique la URL para un recurso de imagen.

   * **[!UICONTROL Texto del cuerpo]**

      Especifique el texto del cuerpo para el intersticial.

   * **[!UICONTROL Confirmar texto]**

      Especifique el texto para el botón de texto.

   * **[!UICONTROL Texto adicional]**

      Especifique el texto alternativo que deba mostrarse.

      Este campo actualiza el botón de texto si falla algún vínculo profundo. Los usuarios son dirigidos a probar el vínculo profundo antes de permitirles ir a otra opción. Por ejemplo, este texto alternativo podría servir para que una tienda de aplicaciones descargue e instale la aplicación o para llevar a los usuarios al sitio web de una compañía. El texto adicional permite a los usuarios saber que hay otra opción disponible si falla el vínculo profundo.


1. (**Optional**) Click the icons above the image to see how the interstitial looks rotated and on different devices.

   Puede cambiar o editar la imagen fuera de Mobile Services para asegurarse de que la imagen se muestra correctamente en distintas situaciones.
1. Haga clic en **[!UICONTROL Guardar]**.
