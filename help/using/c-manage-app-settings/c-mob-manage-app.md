---
description: Puede hacer un seguimiento de los datos que recibe de la aplicación y gestionarlos configurando diversas variables y métricas.
keywords: móvil
solution: Experience Cloud Services,Analytics
title: Gestionar su aplicación
topic-fix: Metrics
uuid: 0cc356c3-8457-40a7-8c97-7cbc68a5dc0c
exl-id: 599fef94-c188-47f5-b9d6-25a7c8cb07bc
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 93%

---

# Gestionar su aplicación {#managing-your-app}

{#eol}

Puede hacer un seguimiento de los datos que recibe de la aplicación y gestionarlos configurando diversas variables y métricas.

## Gestionar variables y métricas  {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **Variables y métricas estándar**

   Cada aplicación incluye variables y métricas para rastrear el carro de compras y las actividades de compra. Parte de la información de las compras no se puede controlar con las reglas de procesamiento, por lo que el SDK expone los datos de contexto especiales de `"&&products"` Por ejemplo: puede tener variables como adiciones al carro de compras, eliminaciones del carro de compras, cierres de compras, pedidos, etc. Los datos de contexto deben asignarse a los datos de Adobe Analytics. Si esta variable se rellena con una asignación simple de datos de contexto, esta es la clave que se asigna. Déjela vacía si unas reglas más complejas rellenan la variable en las Herramientas de administración de Analytics.

* **Variables personalizadas**

   La página Variables personalizadas muestra todas las variables de Analytics personalizadas configuradas para el grupo de informes que contiene los datos de su aplicación. En esta página puede habilitar otras variables y asignar datos de contexto directamente a las variables de Analytics.

### Asignar datos de contexto a las variables de Analytics

Haga clic en **[!UICONTROL Administrar configuración de aplicación]** > **[!UICONTROL Administrar variables y métricas]** > **[!UICONTROL Variables personalizadas]**.

Estas asignaciones llaman a la misma API que [Reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html?lang=es) uso en Adobe Analytics.

![Asignación de datos de contexto](assets/custom_data_content.png)

Esta lista recoge las variables personalizadas que se pueden configurar:

* Las **[!UICONTROL Propiedades personalizadas]** (o props) responden a la pregunta “¿cuál?”. Las props se pueden establecer en un valor de texto que se asociará a otras variables y métricas enviadas en la misma visita. Los valores pueden utilizarse para filtrar informes o pueden enumerarse en orden por métrica asociada.

   Cuando se establece un valor para una propiedad en una llamada de seguimiento (o visita), solo se aplica a esa llamada.

* El **[!UICONTROL Variables personalizadas]** (o eVars) también responden a la pregunta &quot;¿cuál?&quot;. Sin embargo, un valor de eVar no solo se puede aplicar a la visita en la que se envía, sino también a las variables y a las métricas enviadas en las visitas posteriores hasta que el valor caduque o hasta que se defina un nuevo valor.
* Las **[!UICONTROL Variables de lista personalizadas (o variables de valores múltiples)]** se comportan de la misma forma que las variables a excepción de que le permiten capturar varios valores en una visita. Para obtener más información, consulte [lista](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/list.html?lang=es) en la documentación de Adobe Analytics.

Las asignaciones se muestran en Analytics como si se hubieran creado en Mobile Services.

* **[!UICONTROL Nombre]**

   Nombre descriptivo de la variable de colección de datos.

* **[!UICONTROL Datos de contexto]**

   Si esta variable se rellena con una asignación simple de datos de contexto, esta es la clave que se asigna. Deje este campo vacío si más reglas complejas rellenan la variable en las Herramientas de administración de Analytics.

   Haga clic en la columna de datos de contexto y seleccione la variable de datos de contexto que desee asignar. La lista desplegable contiene variables recibidas en los últimos 30 días, por lo que si los datos de contexto que desea asignar no están en la lista, puede escribirlos.

* **[!UICONTROL Persistencia (variables personalizadas y variables de lista personalizadas)]**

   La persistencia determina el punto en el que el valor de una variable personalizada (eVar) caducará o dejará de estar asociado a visitas adicionales. Si una eVar ha caducado cuando se activa una visita, se asociará el valor Ninguno a esa visita para esa eVar. Esto significa que ningún valor de eVar estaba activo cuando se activó la visita.

   Puede seleccionar cualquiera de estas opciones:

   * **[!UICONTROL Session]**

      El valor de eVar persiste durante toda la visita de Analytics.

   * **[!UICONTROL Llamada de seguimiento]**

      El valor de eVar solo persiste durante la llamada de seguimiento o la visita en las que se incluyó.

   * **[!UICONTROL No caducar nunca]**

      El valor de eVar persiste en todas las llamadas de seguimiento subsiguientes.
   * **[!UICONTROL Avanzadas]**

      Adobe Analytics tiene una interfaz de usuario más avanzada para establecer la persistencia de las eVars. Si para la eVar se establece un valor de persistencia que no se admite en Mobile Services, este valor se muestra en la interfaz de usuario de Mobile Services.

      Para gestionar las eVars, haga clic en **[!UICONTROL Administrador del grupo de informes de Adobe Analytics]** > **[!UICONTROL Interfaz de usuario de variables de conversión]**.

   * **[!UICONTROL Compatibilidad de lista]**

      Permite asociar varios valores que se pasan con la propiedad en una única llamada de seguimiento. El delimitador debe ser un carácter único y no puede ser cero o un espacio.

   * **[!UICONTROL Delimitador]**

      El delimitador debe ser un carácter único y no puede ser cero o un espacio.

### Variables adicionales de Analytics

Puede activar variables adicionales en la lista desplegable que hay en la parte inferior de cada sección de variables.

![agregar una variable](assets/add_variable.png)

Seleccione un número de variable no utilizado y escriba un nombre. Opcionalmente, puede proporcionar la variable de datos de contexto que desee almacenar y cualquier información adicional.

* **Métricas personalizadas**

   Las métricas (o los eventos) responden a las preguntas *¿cuánto?* o *¿cuántos?*. Los eventos pueden aumentar cada vez que el usuario realiza una acción o mantener valores numéricos como un precio. Las métricas personalizadas incluyen eventos como la creación de una aplicación, la descarga o exportación del archivo PDF o CSV, el almacenamiento de una campaña, la descarga del SDK, la ejecución de un informe, la adición de un vínculo a la App Store, la activación de un mensaje en la aplicación, etc.

   Seleccione uno de los siguientes tipos de métricas personalizadas:

   * **[!UICONTROL Número entero]**
   * **[!UICONTROL Número decimal]**
   * **[!UICONTROL Moneda]**

## Administrar puntos de interés {#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}

Los puntos de interés permiten definir ubicaciones geográficas que puede utilizar para fines de correlación o para dirigir los mensajes en la aplicación, entre otras opciones. Al enviar una visita en un punto de interés, este se adjunta a la visita. Para obtener más información sobre los puntos de interés, consulte  [Administrar puntos de interés](/help/using/location/t-manage-points.md).

## Administrar destinos de vínculo {#section_F722A387E22A430187B063D358A87711}

Puede crear, editar, archivar/desarchivar y eliminar destinos de vínculos. Estos destinos se pueden invocar en línea cuando se crean vínculos de marketing, notificaciones push o mensajes en aplicaciones. Para obtener más información sobre los destinos de vínculo, consulte [Administrar destinos de vínculo](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md).

## Administrar postbacks {#section_78B0A8D7AE6940E78D85AE3AB829E860}

Los postback permiten enviar datos recopilados por Adobe Mobile a un servidor independiente de terceros. Con los mismos desencadenadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar Mobile para que envíe datos personalizados a un destino de terceros. Para obtener más información sobre los postbacks, consulte  [Configurar los postbacks](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md).
