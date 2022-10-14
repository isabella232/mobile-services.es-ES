---
description: Los postback permiten enviar datos recopilados por Adobe Mobile a un servidor independiente de terceros. Con los mismos desencadenadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar Mobile Services para que envíe datos personalizados a un destino de terceros.
title: Configurar los postbacks
uuid: a026575c-057b-4868-b6c8-9514cbc32b4d
exl-id: 99b27f16-303a-4853-bfdb-2066a53867bf
source-git-commit: dbe3af75010fbf5195a3f93fc43cb696aaa32b65
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 100%

---

# Configurar los postbacks {#configure-postbacks}

Los postback permiten enviar datos recopilados por Adobe Mobile a un servidor independiente de terceros. Con los mismos desencadenadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar Mobile Services para que envíe datos personalizados a un destino de terceros.

>[!IMPORTANT]
>
>Para usar postbacks, debe instalar el SDK 4.6 o posteriores.

1. Haga clic en el nombre de la aplicación que quiera para acceder a la página Administrar configuración de aplicación y haga clic en **[!UICONTROL Administrar postbacks]** en la parte superior derecha.
2. Haga clic en **[!UICONTROL Crear postback]**.
3. Escriba la información siguiente en los campos:

   * **[!UICONTROL Tipo de postback]**

      Elija **[!UICONTROL Personalizado]**. Próximamente habrá plantillas disponibles.

   * **[!UICONTROL Nombre]**

      Especifique un nombre descriptivo para el postback.

   * **[!UICONTROL Dirección URL]**

      Especifique una URL de punto final válida (con los parámetros de consulta adecuados que se necesitan en las solicitudes GET). Puede obtener esta URL de la parte a la que envía los datos (servidor de publicidad o su propio punto final). Por ejemplo `https://example.com/?user=bob&amp;zip=90210&amp;c16=4.6.0-iOS&amp;c27=cln,132`.

   * **[!UICONTROL Variable de contexto]**

      Resalte partes de la URL y seleccione la variable de contexto que desee en la lista desplegable. También puede insertar variables de contexto en la dirección URL, y esta sustituirá todas las variables de plantilla por valores de la visita.

   * **[!UICONTROL Agregar cuerpo del anuncio]**

      Especifique contenido del cuerpo del anuncio adicional, como en una solicitud de post. Si especifica el texto del cuerpo del anuncio, especifique el tipo de contenido de este. Por ejemplo, `application/json`.

   * **[!UICONTROL Tiempo de espera (en segundos)]**

      Especifique el tiempo (en segundos) de espera para el postback.

   * **[!UICONTROL Activador(es)]**

      Especifique una o varias etiquetas de datos y condiciones que activen el postback. Por ejemplo, puede elegir **[!UICONTROL Bloqueado]** como activador y **[!UICONTROL Existe]** como condición para activar el postback en caso de que la aplicación se bloquee. También puede especificar qué métricas activan el postback. Por ejemplo, puede elegir **[!UICONTROL Nombre del dispositivo]** como activador y **[!UICONTROL Es igual a]** y **[!UICONTROL iPhone 6 Plus]** como condiciones para activar el postback en caso de que la aplicación se bloquee en dispositivos iPhone 6 Plus.

   * **[!UICONTROL Característica(s)]**
   Especifique quién puede ver el mensaje cuando se activa. Las opciones son **[!UICONTROL Duración de la sesión]**, **[!UICONTROL Primera fecha de inicio]** e **[!UICONTROL ID de aplicación]**.

4. Haga clic en **[!UICONTROL Guardar]** para crear el postback y agregarlo a la lista **[!UICONTROL Administrar postbacks]**.

   Para activar el postback en el futuro, siga uno de estos pasos:

   * Seleccione la casilla que hay junto al postback en la lista **[!UICONTROL Administrar postbacks]** y haga clic en **[!UICONTROL Activar seleccionados]**.
   * Haga clic en **[!UICONTROL Guardar y activar]** para guardar los cambios y activar el postback inmediatamente.
