---
description: Después de agregar la biblioteca al proyecto, puede realizar cualquier llamada a un método de Analytics desde cualquier punto de su aplicación (asegúrese de importar ADBMobile.h en su clase).
seo-description: Después de agregar la biblioteca al proyecto, puede realizar cualquier llamada a un método de Analytics desde cualquier punto de su aplicación (asegúrese de importar ADBMobile.h en su clase).
seo-title: Analytics
title: Analytics
uuid: de 018 eda-b 37 d -4 afe -83 a 0-8011381 d 7 aff
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

Después de agregar la biblioteca al proyecto, puede realizar cualquier llamada a un método de Analytics desde cualquier punto de su aplicación (asegúrese de importar ADBMobile.h en su clase).

## Enable mobile application reports in Analytics {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Antes de añadir código, pida a su administrador de Analytics que complete los siguientes pasos para habilitar el seguimiento de ciclo vital de aplicaciones móviles. Esto garantiza que su grupo de informes esté listo para capturar métricas cuando comience el desarrollo.


1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).
1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Haga clic en **[!UICONTROL Habilitar los informes de aplicaciones más recientes]**.

   Opcionalmente, también puede hacer clic en **[!UICONTROL Activar el seguimiento de ubicación móvil]** y en **[!UICONTROL Habilitar el uso de informes anteriores y la atribución de resultados en segundo plano]**.

   ![](assets/enable-lifecycle.png)

Lifecycle metrics are now ready to be captured, and Mobile Application Reports] appear in the **[!UICONTROL Reports]** menu in the marketing reports interface.

## Recopilación de métricas del ciclo vital {#task_25D469C62DF84573AEB5E8E950B96205}

1. To collect lifecycle metrics in your app, call `collectLifecycleData()` in the `ApplicationUI` constructor.

   Por ejemplo:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   If `collectLifecycleData()` is called twice in the same session, then your application will report a crash on every call after the first. Cuando la aplicación se cierra, el SDK establece un indicador que especifica una salida correcta. If this flag is not set, `collectLifecyleData()` reports a crash.

## Events, props, and eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


Si ha consultado la Referencia de métodos y clases [adbmobile](/help/blackberry/methods.md), probablemente se esté preguntando dónde configurar eventos, evars, props, herederos y listas. En la versión 4, ya no puede asignar estos tipos de variables directamente en la aplicación. Ahora el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de su aplicación a variables de Analytics de cara a la realización de informes.

Las reglas de procesamiento ofrecen varias ventajas:

* Puede cambiar la asignación de datos sin tener que enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos, en vez de establecer variables específicas para un grupo de informes.
* El impacto de enviar los datos extra es ínfimo. Estos valores no aparecen en los informes hasta que se los asigna mediante reglas de procesamiento.

Los valores que asignaba directamente a variables deberán añadirse al HashMap `data`.

## Reglas de procesamiento {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a eVars, props y otras variables con el fin de realizar informes.

[Formación de reglas de procesamiento](https://tv.adobe.com/embed/1181/16506/) en Summit 2013

[Reglas de procesamiento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Obtener autorización para utilizar reglas de procesamiento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Se recomienda agrupar las variables de datos de contexto mediante “espacios de nombres”, ya que esto ayuda a mantener una ordenación lógica. Por ejemplo, si quiere recopilar información acerca de un producto, podría definir las siguientes variables:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Las variables de datos de contexto se ordenan alfabéticamente en la interfaz de reglas de procesamiento, de modo que los espacios de nombres le permiten ver rápidamente qué variables hay en el mismo espacio de nombres.

Además, hay quien asigna nombres a las claves de datos de contexto empleando el número de eVar o prop:

```js
"eVar1":"jimbo"
```

Esto podría ayudarle *un poco* a la hora de llevar a cabo la asignación que hay que realizar una única vez en las reglas de procesamiento, a costa de perder legibilidad durante la depuración y las futuras actualizaciones de código, que pueden resultarle más difíciles. En su lugar, lo que se recomienda encarecidamente es utilizar nombres descriptivos para las claves y los valores:

```js
"username":"jimbo"
```

Las variables de contexto que definen eventos de contador pueden tener el mismo valor y clave:

```js
"logon":"logon"
```

Las variables de contexto que definen eventos de aumento pueden tener el evento como clave y la cantidad que se debe incrementar como valor:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe se reserva el espacio de nombres `a.`. Aparte de esta pequeña restricción, las variables de datos de contexto solo tienen que ser exclusivas en su empresa de inicio de sesión para evitar conflictos.

## Habilitar el seguimiento sin conexión {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

To store hits when the device is offline, you can optionally enable offline tracking in the `ADBMobileConfig.json` file.

Preste mucha atención a los requisitos de marca de fecha y hora que se describen en la referencia del archivo de configuración antes de habilitar el seguimiento sin conexión.

## Métodos de Analytics

Para obtener una lista de los métodos de Analytics disponibles para blackberry, consulte *Métodos de Analytics* en [Referencia de métodos y clases móviles de Adobe](/help/blackberry/methods.md).