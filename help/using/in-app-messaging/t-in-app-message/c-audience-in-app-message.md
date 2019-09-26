---
description: Puede configurar las opciones de audiencia para los mensajes en la aplicación, incluidas las opciones de visualización, activadores y características.
keywords: móvil
seo-description: Puede configurar las opciones de audiencia para los mensajes en la aplicación, incluidas las opciones de visualización, activadores y características.
seo-title: Mensaje de audiencia en la aplicación
solution: Marketing Cloud,Analytics
title: Mensaje de audiencia en la aplicación
topic: Métricas
uuid: 6c815d4c-7626-4cf4-9158-3f059c79317a
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Audience: in-app message {#audience-in-app-message}

Puede configurar las opciones de audiencia para los mensajes en la aplicación, incluidas las opciones de visualización, activadores y características.

1. In your app, click **[!UICONTROL Messaging]** &gt; **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]** &gt; **[!UICONTROL Create In-App]**.
1. En la página Audiencia, rellene los campos siguientes:

   * **[!UICONTROL Ver]**

      Seleccione la opción que activa la visualización de un mensaje:

      * **[!UICONTROL Siempre]**

         Con esta opción, el mensaje se muestra siempre que se produce la activación.

      * **[!UICONTROL Una vez]**

         Con esta opción, el mensaje se muestra solo la primera vez que se produce la activación.

      * **[!UICONTROL Hasta la pulsación]**

         Con esta opción, el mensaje se muestra siempre que se produce la activación hasta que el usuario hace clic. Esta activación solo se aplica en la pantalla completa y los mensajes de alerta. La mayoría de los mensajes tienen que redireccionarse o emplear un recurso de Internet y no se muestran si no hay conexión. Para mostrar siempre el mensaje, con independencia de la conectividad de red, seleccione la casilla de verificación **[!UICONTROL Mostrar sin conexión].**
   * **[!UICONTROL Activador]**

      Seleccione una opción en la lista desplegable y elija una condición. Por ejemplo, puede seleccionar **[!UICONTROL Iniciado]** en la primera lista desplegable y **Existe]en la segunda.[!UICONTROL ** También puede especificar datos de contexto personalizados que tengan que estar en la visita de activación para mostrar el mensaje.

      >[!IMPORTANT]
      >
      >Si selecciona varios activadores para que se muestre el mensaje, todos los activadores deben producirse en la misma visita.

   * **[!UICONTROL Traits]**
You can determine who should see the in-app message when it is triggered and filter (segment) the audience to hits that have specified data. Por ejemplo, puede definir una regla en la que Puntos de interés contenga Denver. Este filtro permite mostrar, en el momento de la activación, el mensaje a los clientes que estén en uno de los puntos de interés con Denver en el nombre.



## Additional information about traits and triggers {#section_48C39EFB8CAA4F62B994FCC91DF588E6}

>[!IMPORTANT]
>
>Los activadores y las características utilizan datos que se pasan a Analytics desde la aplicación. Estos valores se pasan como datos contextuales, variables asignadas y métricas. Una variable es un valor basado en texto y una métrica es un valor numérico.

To see the mapping of these key value pairs in the Mobile Services UI and validate the value for your trigger, click **[!UICONTROL Manage App Settings]** &gt;  **[!UICONTROL Manage Variables &amp; Metrics]** &gt;, which displays the following tabs:

* **[!UICONTROL Variables y métricas estándar]**
* **[!UICONTROL Variables personalizadas]**
* **[!UICONTROL Métricas personalizadas]**

Después de validar la asignación, seleccione el valor coincidente apropiado o el operador lógico para configurar su audiencia para el mensaje.

### Selecting metrics and variables {#example_AB126F03BD1C4094B791E230B3DB1189}

![activar opciones](assets/custom_trigger_matcher_options.png)

Los escenarios siguientes le ayudan a determinar si desea seleccionar una métrica o una variable como activador:

### Métricas

Una métrica es un número y un ejemplo es el número de compras.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Complete los siguientes pasos en la sección **[!UICONTROL Activador]** en la pestaña **Audiencia[!UICONTROL :]**

   1. Seleccione un evento estándar como **[!UICONTROL Iniciado]** y seleccione **[!UICONTROL Existe]**.
   1. Seleccione un segundo activador que es un punto de datos personalizado y que está asignado a una métrica.
   1. Under **[!UICONTROL Number]**, select a matcher option.

### Variables

Una variable es una cadena de texto que es un identificador único, por ejemplo, país, aeropuerto, etc.

1. Click **[!UICONTROL Manage Messages]** &gt; **[!UICONTROL Create Message]**.
1. Complete los siguientes pasos en la sección **[!UICONTROL Activador]** en la pestaña **Audiencia[!UICONTROL :]**

   1. Seleccione un evento estándar como **[!UICONTROL Iniciado]** y seleccione **[!UICONTROL Existe]**.
   1. Seleccione un segundo activador que es un punto de datos personalizado y que está asignado a una variable.
   1. Under **[!UICONTROL Text]**, select a matcher option.

For more information about context data, variables, and metrics, see [Managing your app](/help/using/manage-apps/manage-apps.md).
