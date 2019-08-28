---
description: Los postbacks permiten enviar datos recopilados por Adobe Mobile a un servidor independiente de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar Mobile Services para que envíe datos personalizados a un destino de terceros.
seo-description: Los postbacks permiten enviar datos recopilados por Adobe Mobile a un servidor independiente de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar Mobile Services para que envíe datos personalizados a un destino de terceros.
seo-title: Configurar los postbacks
title: Configurar los postbacks
uuid: a 026575 c -057 b -4868-b 6 c 8-9514 cbc 32 b 4 d
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configure postbacks {#configure-postbacks}

Los postbacks permiten enviar datos recopilados por Adobe Mobile a un servidor independiente de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar Mobile Services para que envíe datos personalizados a un destino de terceros.

>[!IMPORTANT]
>
>Para utilizar postbacks, debe instalar el SDK 4.6 o posterior. Para obtener más información, consulte [Android: Postback](/help/android/analytics-main/postbacks/postbacks.md) o [iOS: Postback](/help/ios/analytics-main/postback/postback.md).

1. Haga clic en el nombre de la aplicación que quiera para acceder a la página Administrar configuración de aplicación y haga clic en **Administrar postbacks** en la parte superior derecha.
1. Haga clic en **[!UICONTROL Crear postback]**.
1. Escriba la información siguiente en los campos:

   * **[!UICONTROL Tipo de postback]**

      Elija **[!UICONTROL Personalizado]**. Próximamente habrá plantillas disponibles.

   * **[!UICONTROL Nombre]**

      Especifique un nombre descriptivo para el postback.

   * **[!UICONTROL Dirección URL]**

      Especifique una URL de extremo válida (con los parámetros de consulta adecuados según se requiera para las solicitudes GET). Puede obtener esta URL de la parte a la que envía los datos (servidor de publicidad o su propio extremo). Por ejemplo `https://my.server.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Variable de contexto]**

      Resalte partes de la URL y seleccione la variable de contexto que desee en la lista desplegable. También puede insertar variables de contexto en la URL y la dirección URL sustituirá a todas las variables de plantilla con valores de la visita.

   * **[!UICONTROL Agregar cuerpo del anuncio]**

      Especifique contenido del cuerpo del anuncio adicional, como en una solicitud de post. Si especifica texto del cuerpo del anuncio, especifique el tipo de contenido del cuerpo del anuncio. Por ejemplo, `application/json`.

   * **[!UICONTROL Tiempo de espera (en segundos)]**

      Especifique el tiempo (en segundos) de espera para el postback.

   * **[!UICONTROL Activador(es)]**

      Especifique una o varias etiquetas de datos y condiciones que activen el postback. For example, you might choose **[!UICONTROL Crashed]** as the trigger and **[!UICONTROL Exists]** as the condition to trigger the postback when the app crashes. También puede especificar qué métricas activan el postback. For example, you can select **[!UICONTROL Device Name]** as the trigger, **[!UICONTROL Equals]**, and **[!UICONTROL iPhone 6 Plus]** as conditions to activate the postback when the app crashes on iPhone 6 Plus devices.

   * **[!UICONTROL Característica(s)]**
   Especifique quién puede ver el mensaje cuando se activa. Options include **[!UICONTROL Session Length**, **[!UICONTROL First Launch Date]**, and **[!UICONTROL App ID]**.

1. Haga clic en **[!UICONTROL Guardar]** para crear el postback y agregarlo a la lista **Administrar postbacks[!UICONTROL .]**

   Para activar el postback en el futuro, siga uno de estos pasos:

   * Seleccione la casilla que hay junto al postback en la lista **[!UICONTROL Administrar postbacks]** y haga clic en **[!UICONTROL Activar seleccionados]**.
   * Haga clic en **[!UICONTROL Guardar y activar]para guardar los cambios y activar el postback inmediatamente.**
