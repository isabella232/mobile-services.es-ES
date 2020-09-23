---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Experience Cloud,Analytics
title: Analytics
topic: Developer and implementation
uuid: c2cef3d3-77a7-4a8e-bbe4-3db10a77996a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 11%

---


# Analytics {#analytics}

Después de agregar la biblioteca al proyecto, puede realizar cualquiera de las llamadas de método de Analytics en cualquier parte de la aplicación.

>[!TIP]
>
>Asegúrese de importar `ADBMobile.h` a la clase.

## Habilitar informes de aplicaciones móviles en Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Antes de agregar código, pida al administrador de Analytics que complete lo siguiente para habilitar el seguimiento del ciclo vital de las aplicaciones móviles. Esto garantiza que el grupo de informes esté listo para capturar métricas a medida que comienza el desarrollo.

1. Abra Herramientas **[!UICONTROL de administración]** > Grupos **[!UICONTROL de informes]** y seleccione los grupos de informes móviles.

1. Haga clic en **[!UICONTROL Editar configuración]** > Administración **** móvil > Sistema de informes **[!UICONTROL de aplicaciones]** móviles.

   ![](assets/mobile-settings.png)

1. Haga clic en **[!UICONTROL Habilitar los informes]** de aplicación más recientes.

   También puede hacer clic en **[!UICONTROL Activar el seguimiento]** de ubicación móvil o en **[!UICONTROL Activar el Sistema de informes y la atribución heredados para las visitas]** en segundo plano.

   ![](assets/enable-lifecycle.png)

Las métricas del ciclo vital ya están listas para capturarse y los informes de aplicaciones móviles aparecen en el menú **[!UICONTROL Informes]** de la interfaz de informes de marketing.

### Nuevas versiones

Periódicamente, se lanzan nuevas versiones del sistema de informes de aplicaciones móviles. Las nuevas versiones no se aplican al grupo de informes automáticamente, debe repetir estos pasos para realizar la actualización. Cada vez que agregue una nueva funcionalidad de Experience Cloud a su aplicación, le recomendamos que repita estos pasos para asegurarse de que dispone de la configuración más reciente.

## Métricas del ciclo vital {#section_532702562A7A43809407C9A2CBA80E1E}

Para recopilar métricas del ciclo vital en la aplicación, agregue llamadas al momento en que la aplicación se activa, como se muestra en los ejemplos siguientes.

### WinJS en default.js

```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### C# en App.xaml.cs

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming += OnResuming; 
    this.Suspending += OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{   ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### C++/CX en App.xaml.cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming += ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending += ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

Si `CollectLifecycleData()` se llama dos veces en la misma sesión, la aplicación informa de un bloqueo en cada llamada después de la primera. El SDK establece un indicador cuando se cierra la aplicación que indica una salida correcta. Si no se establece este indicador, `CollectLifecyleData()` informa de un bloqueo.

## Eventos, props y eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

Si ha observado los métodos [](/help/universal-windows/c-configuration/methods.md)SDK, probablemente se esté preguntando dónde establecer eventos, eVars, props, herederos y listas. En la versión 4, ya no puede asignar estos tipos de variables directamente en la aplicación. En su lugar, el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de la aplicación a variables de Analytics para sistema de informes.

Las reglas de procesamiento ofrecen varias ventajas:

* Puede cambiar la asignación de datos sin enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos en lugar de establecer variables específicas de un grupo de informes.
* El envío de datos adicionales tiene poco impacto. Estos valores no aparecerán en los informes hasta que se asignen mediante reglas de procesamiento.

Los valores que asignaba directamente a variables deberían agregarse a los datos de contexto.

## Reglas de procesamiento {#section_66EE762EEA5E4728864166201617DEBF}

Las reglas de procesamiento se utilizan para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables para sistema de informes.

[Formación](https://tv.adobe.com/embed/1181/16506/) sobre reglas de procesamiento en Summit 2013

[Ayuda de reglas de procesamiento](https://docs.adobe.com/content/help/es-ES/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Obtener autorización para utilizar reglas de procesamiento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Recomendamos agrupar las variables de datos de contexto mediante &quot;Áreas de nombres&quot;, ya que esto le ayuda a mantener un orden lógico. Por ejemplo, si desea recopilar información sobre un producto, puede definir las siguientes variables:

```javascript
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

Configure variables de contexto que definan eventos de contador con un valor de &quot;1&quot;:

```js
"logon":"1"
```

Las variables de datos de contexto que definen eventos de aumento pueden tener el valor que incrementar:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe reserva el espacio de nombres `a.`. Aparte de esta restricción, las variables de datos de contexto solo deben ser únicas en la compañía de inicio de sesión para evitar conflictos.

## Variable Products {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Para establecer *`products`* en el SDK móvil, debe utilizar una sintaxis especial. Para obtener más información, consulte Variable [](/help/universal-windows/analytics/products.md)Productos.

## (Opcional) Habilitar el seguimiento sin conexión {#section_955B2A03EB854742BDFC4A0A3C287009}

Para almacenar visitas cuando el dispositivo está sin conexión, puede activar el seguimiento sin conexión en el archivo de métodos [](/help/universal-windows/c-configuration/methods.md) SDK. Antes de habilitar el seguimiento sin conexión, preste especial atención a los requisitos de marca de hora descritos en la referencia del archivo de configuración.

## Geolocalización y puntos de interés {#section_BAD34A8DD013454DB355121316BD7FD4}

La geolocalización permite medir datos de ubicación (latitud/longitud) y puntos de interés predefinidos. Cada `TrackLocation` llamada envía:

* Latitud/Longitud y puntos de interés (si se encuentra dentro de un punto de interés definido en el archivo `ADBMobileConfig.json` de configuración).

   Se pasan a variables de soluciones móviles para sistema de informes automático.

* Distancia desde el centro y precisión pasados como datos de contexto.

   Capturar mediante una regla de procesamiento.

Para rastrear una ubicación:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Si el siguiente punto de interés está definido en el archivo `ADBMobileConfig.json` de configuración:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

Cuando se determina que la ubicación del dispositivo está dentro de un radio de 7000 metros del punto definido, se envía una variable de datos de `a.loc.poi` contexto con el valor `San Francisco` junto con la `TrackLocation` visita. An `a.loc.dist` context variable is sent with the distance in meters from the defined coordinates.

## Lifetime value {#section_D2C6971545BA4D639FBE07F13EF08895}

El valor de duración le permite medir y tomar como destino un valor de duración para cada usuario. Cada vez que envía un valor con `TrackLifetimeValueIncrease`, el valor se agrega al valor existente. El valor de duración se almacena en el dispositivo y se puede recuperar en cualquier momento realizando una llamada a `GetLifetimeValue`. Esto puede utilizarse para almacenar compras acumuladas en el tiempo, visualizaciones de anuncios, visualizaciones de vídeo completas, usos compartidos en medios sociales, cargas de fotografías, etc.

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## Acciones temporizadas {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

Las acciones temporizadas le permiten medir el tiempo dentro de la aplicación y el tiempo total entre el inicio y el final de una acción. El SDK calcula la cantidad de tiempo en la sesión y el tiempo total (entre sesiones) que tarda la acción en completarse. Esto se puede usar para definir segmentos que comparar en el tiempo de compra, nivel de paso, flujo de cierre de compra, etc.

* Total de segundos en la aplicación entre inicio y final: entre sesiones
* Total de segundos entre el inicio y el final (hora del reloj)

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```
