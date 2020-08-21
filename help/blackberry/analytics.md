---
description: Después de agregar la biblioteca al proyecto, puede realizar cualquiera de las llamadas de método de Analytics en cualquier parte de la aplicación (asegúrese de importar ADBMobile.h a la clase).
seo-description: Después de agregar la biblioteca al proyecto, puede realizar cualquiera de las llamadas de método de Analytics en cualquier parte de la aplicación (asegúrese de importar ADBMobile.h a la clase).
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 5%

---


# Analytics {#analytics}

Después de agregar la biblioteca al proyecto, puede realizar cualquiera de las llamadas de método de Analytics en cualquier parte de la aplicación (asegúrese de importar ADBMobile.h a la clase).

## Habilitar informes de aplicaciones móviles en Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Antes de agregar código, pida al administrador de Analytics que complete lo siguiente para habilitar el seguimiento del ciclo vital de las aplicaciones móviles. Esto garantiza que el grupo de informes esté listo para capturar métricas a medida que comienza el desarrollo.


1. Abra Herramientas **[!UICONTROL de administración]** > Grupos **[!UICONTROL de informes]** y seleccione los grupos de informes móviles.
1. Haga clic en **[!UICONTROL Editar configuración]** > Administración **** móvil > Sistema de informes **[!UICONTROL de aplicaciones]** móviles.

   ![](assets/mobile-settings.png)

1. Haga clic en **[!UICONTROL Habilitar los informes]** de aplicación más recientes.

   También puede hacer clic en **[!UICONTROL Activar el seguimiento]** de ubicación móvil y **[!UICONTROL Activar el Sistema de informes y la atribución heredados para las visitas]** en segundo plano.

   ![](assets/enable-lifecycle.png)

Las métricas del ciclo vital ya están listas para capturarse y los informes de aplicaciones móviles aparecen en el menú **[!UICONTROL Informes]** de la interfaz de informes de marketing.

## Recopilar métricas del ciclo vital {#task_25D469C62DF84573AEB5E8E950B96205}

1. Para recopilar métricas del ciclo vital en la aplicación, llame `collectLifecycleData()` al `ApplicationUI` constructor.

   Por ejemplo:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Si `collectLifecycleData()` se llama dos veces en la misma sesión, la aplicación informará de un bloqueo en cada llamada después de la primera. El SDK establece un indicador cuando se cierra la aplicación que indica una salida correcta. Si no se establece este indicador, `collectLifecyleData()` informa de un bloqueo.

## Eventos, props y eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


Si ha observado la Referencia [de métodos y clases](/help/blackberry/methods.md)ADBMobile, probablemente se pregunte dónde establecer eventos, eVars, propiedades, herederos y listas. En la versión 4, ya no puede asignar estos tipos de variables directamente en la aplicación. En su lugar, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para sistema de informes.

Las reglas de procesamiento ofrecen varias ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto. Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento.

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## Reglas de procesamiento {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Las reglas de procesamiento se utilizan para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables para sistema de informes.

[Formación](https://tv.adobe.com/embed/1181/16506/) sobre reglas de procesamiento en Summit 2013

[Reglas de procesamiento](https://docs.adobe.com/content/help/es-ES/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Obtenga autorización para utilizar reglas de procesamiento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Recomendamos agrupar las variables de datos de contexto mediante &quot;Áreas de nombres&quot;, ya que esto le ayuda a mantener un orden lógico. Por ejemplo, si desea recopilar información sobre un producto, puede definir las siguientes variables:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Las variables de datos de contexto se ordenan alfabéticamente en la interfaz de reglas de procesamiento, por lo que las Áreas de nombres permiten ver rápidamente las variables que están en la misma Área de nombres.

Además, hemos oído que algunos de ustedes están nombrando claves de datos de contexto usando el número de eVar o prop:

```js
"eVar1":"jimbo"
```

Esto puede hacer que sea *ligeramente* más fácil cuando se realiza la asignación de una sola vez en las reglas de procesamiento, pero la legibilidad durante la depuración y las futuras actualizaciones de código pueden resultar más difíciles. En su lugar, recomendamos encarecidamente utilizar nombres descriptivos para claves y valores:

```js
"username":"jimbo"
```

Las variables de contexto que definen eventos de contador pueden tener la misma clave y el mismo valor:

```js
"logon":"logon"
```

Las variables de datos de contexto que definen eventos de aumento pueden tener el evento como clave y la cantidad que se incrementará como valor:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe reserva el espacio de nombres `a.`. Aparte de esta pequeña restricción, las variables de datos de contexto solo deben ser únicas en la compañía de inicio de sesión para evitar conflictos.

## Habilitar seguimiento sin conexión {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Para almacenar visitas cuando el dispositivo está sin conexión, puede activar el seguimiento sin conexión en el `ADBMobileConfig.json` archivo.

Preste mucha atención a los requisitos de marca de hora descritos en la referencia del archivo de configuración antes de habilitar el seguimiento sin conexión.

## Métodos de Analytics

Para obtener una lista de los métodos de Analytics disponibles para BlackBerry, consulte Métodos *de* Analytics en Referencia [de métodos y clases móviles de](/help/blackberry/methods.md)Adobe.