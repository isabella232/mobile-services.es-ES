---
description: Después de agregar la biblioteca al proyecto, puede realizar cualquiera de las llamadas de método de Analytics en cualquier parte de la aplicación (asegúrese de importar ADBMobile.h a su clase).
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
exl-id: 4cd27e1a-e806-4dbb-84f5-63902ca2003f
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 12%

---

# Analytics {#analytics}

Después de agregar la biblioteca al proyecto, puede realizar cualquiera de las llamadas de método de Analytics en cualquier parte de la aplicación (asegúrese de importar ADBMobile.h a su clase).

## Habilitar los informes de aplicaciones móviles en Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Antes de agregar código, pida a su administrador de Analytics que complete lo siguiente para habilitar el seguimiento del ciclo vital de las aplicaciones móviles. Estas acciones garantizan que el grupo de informes esté listo para capturar métricas a medida que comience el desarrollo.

1. Abra **[!UICONTROL Herramientas de administración]** > **[!UICONTROL Grupos de informes]** y seleccione los grupos de informes móviles.
1. Haga clic en **[!UICONTROL Editar configuración]** > **[!UICONTROL Administración de móviles]** > **[!UICONTROL Informes de aplicaciones móviles]**.

   ![Configuración móvil](assets/mobile-settings.png)

1. Haga clic en **[!UICONTROL Habilitar los informes de aplicaciones más recientes]**.

   De forma opcional, también puede hacer clic en **[!UICONTROL Habilitar el seguimiento de ubicación móvil]** y **[!UICONTROL Habilitar el sistema de informes y la atribución anteriores para las visitas en segundo plano]**.

   ![Habilitar ciclo vital](assets/enable-lifecycle.png)

Las métricas del ciclo vital ya están listas para capturarse, e Informes de aplicaciones móviles aparece en el menú **[!UICONTROL Informes]** de la interfaz de informes de marketing.

## Recopilar métricas del ciclo vital {#task_25D469C62DF84573AEB5E8E950B96205}

1. Para recopilar métricas del ciclo vital en la aplicación, llame a `collectLifecycleData()` en el constructor `ApplicationUI`.

   Por ejemplo:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Si se llama a `collectLifecycleData()` dos veces en la misma sesión, la aplicación informará de un bloqueo en cada llamada posterior a la primera. El SDK establece un indicador cuando la aplicación se cierra, que indica una salida correcta. Si no se establece este indicador, `collectLifecyleData()` informa de un bloqueo.

## Eventos, props y eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}

Si ha consultado la [Referencia de métodos y clases ADBMobile](/help/blackberry/methods.md), probablemente se esté preguntando dónde configurar eventos, eVars, props, herederos y listas. En la versión 4, ya no puede asignar estos tipos de variables directamente en la aplicación. En su lugar, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para el sistema de informes.

Las reglas de procesamiento ofrecen varias ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización a la tienda de aplicaciones.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto. Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento.

Cualquier valor que asignara directamente a variables debe agregarse al HashMap `data` en su lugar.

## Reglas de procesamiento {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Las reglas de procesamiento se utilizan para copiar los datos que envía en variables de datos de contexto a eVars, props y otras variables con el fin de realizar informes.

[Reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)

Adobe recomienda agrupar las variables de datos de contexto mediante &quot;áreas de nombres&quot;, ya que esto le ayuda a mantener un orden lógico. Por ejemplo, si desea recopilar información sobre un producto, puede definir las siguientes variables:

```js
"product.type":"hat";
"product.team":"mariners";
"product.color":"blue";
```

Las variables de datos de contexto se ordenan alfabéticamente en la interfaz de reglas de procesamiento, por lo que los espacios de nombres permiten ver rápidamente las variables que están en el mismo espacio de nombres.

Además, hemos oído que algunos de ustedes están nombrando claves de datos de contexto usando el número de eVar o propiedad:

```js
"eVar1":"jimbo";
```

Esto puede facilitar *ligeramente* la tarea de asignar de una sola vez en las reglas de procesamiento, pero se pierde la legibilidad durante la depuración y las futuras actualizaciones de código pueden resultar más difíciles. En su lugar, se recomienda encarecidamente utilizar nombres descriptivos para claves y valores:

```js
"username":"jimbo";
```

Las variables de contexto que definen eventos de contador pueden tener la misma clave y valor:

```js
"logon":"logon";
```

Las variables de datos de contexto que definen eventos de aumento pueden tener el evento como clave y la cantidad que se incrementará como valor:

```js
"levels completed":"6";
```

>[!TIP]
>
>Adobe reserva el espacio de nombres `a.`. Aparte de esta pequeña restricción, las variables de datos de contexto solo deben ser exclusivas en su empresa de inicio de sesión para evitar conflictos.

## Habilitar el seguimiento sin conexión {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Para almacenar visitas cuando el dispositivo está sin conexión, puede habilitar el seguimiento sin conexión en el archivo `ADBMobileConfig.json`.

Preste mucha atención a los requisitos de marca de tiempo descritos en la referencia del archivo de configuración antes de habilitar el seguimiento sin conexión.

## Métodos de Analytics

Para obtener una lista de los métodos de Analytics disponibles para BlackBerry, consulte *Métodos de Analytics* en [Referencia de métodos y clases móviles de Adobe](/help/blackberry/methods.md).
