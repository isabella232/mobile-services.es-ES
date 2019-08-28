---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Marketing Cloud, Analytics
title: Analytics
topic: Desarrollador e implementación
uuid: c 2 cef 3 d 3-77 a 7-4 a 8 e-bbe 4-3 db 10 a 77996 a
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

Después de agregar la biblioteca a su proyecto, puede hacer que cualquiera de los métodos de Analytics realice llamadas en cualquier parte de la aplicación.

>[!TIP]
>
>Asegúrese de importar `ADBMobile.h` a la clase.

## Enable mobile application reports in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Antes de añadir código, pida a su administrador de Analytics que complete los siguientes pasos para habilitar el seguimiento de ciclo vital de aplicaciones móviles. Esto garantiza que su grupo de informes esté listo para capturar métricas cuando comience el desarrollo.

1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).

1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Haga clic en **[!UICONTROL Habilitar los informes de aplicaciones más recientes]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** or **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

Ya se pueden capturar las métricas del ciclo vital, e Informes de aplicaciones móviles aparece en el menú **Informes** de la interfaz de informes de marketing.

### Versiones nuevas

Se lanzan nuevas versiones de los informes de aplicaciones móviles de forma periódica. Estas versiones no se aplican automáticamente a su grupo de informes, debe repetir estos pasos para realizar la actualización. Recomendamos repetir estos pasos cada vez que añada nuevas funciones de Experience Cloud a la aplicación para garantizar que dispone de la configuración más reciente.

## Lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

Para recopilar métricas del ciclo vital en la aplicación, añada llamadas que se activen cuando lo haga la aplicación, como se muestra en los ejemplos siguientes.

### Winjs en default. js

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

### C # en App. xaml. cs

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

If `CollectLifecycleData()` is called twice in the same session, your application reports a crash on every call after the first. Cuando la aplicación se cierra, el SDK establece un indicador que especifica una salida correcta. If this flag is not set, `CollectLifecyleData()` reports a crash.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

If you've looked at [SDK methods](/help/universal-windows/c-configuration/methods.md), you are probably wondering where to set events, eVars, props, heirs, and lists. En la versión 4, ya no puede asignar estos tipos de variables directamente en la aplicación. Ahora el SDK utiliza datos de contexto y reglas de procesamiento para asignar los datos de su aplicación a variables de Analytics de cara a la realización de informes.

Las reglas de procesamiento ofrecen varias ventajas:

* Puede cambiar la asignación de datos sin tener que enviar una actualización al App Store.
* Puede utilizar nombres significativos para los datos, en vez de establecer variables específicas para un grupo de informes.
* El impacto de enviar los datos extra es ínfimo. Estos valores no aparecen en los informes hasta que se los asigna mediante reglas de procesamiento.

Cualquier valor que asignara directamente a variables debe agregarse a los datos de contexto.

## Reglas de procesamiento {#section_66EE762EEA5E4728864166201617DEBF}

Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a eVars, props y otras variables con el fin de realizar informes.

[Formación de reglas de procesamiento](https://tv.adobe.com/embed/1181/16506/) en Summit 2013

[Ayuda de las reglas de procesamiento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Obtenga autorización para utilizar reglas de procesamiento](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Se recomienda agrupar las variables de datos de contexto mediante “espacios de nombres”, ya que esto ayuda a mantener una ordenación lógica. Por ejemplo, si quiere recopilar información acerca de un producto, podría definir las siguientes variables:

```javascript
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Las variables de datos de contexto se ordenan alfabéticamente en la interfaz de reglas de procesamiento, de modo que los espacios de nombres le permiten ver rápidamente qué variables hay en el mismo espacio de nombres.

Además, hay quien asigna nombres a las claves de datos de contexto empleando el número de eVar o prop:

```js
"eVar1":"jimbo"
```

Esto podría ayudarle *un poco* a la hora de llevar a cabo la asignación que hay que realizar una única vez en las reglas de procesamiento, a costa de perder legibilidad durante la depuración y las futuras actualizaciones de código, que pueden resultarle más difíciles. Lo que se recomienda encarecidamente es utilizar nombres descriptivos para las claves y valores:

```js
"username":"jimbo"
```

Establezca variables de contexto que definan para los eventos de contador un valor de “1”:

```js
"logon":"1"
```

Las variables de datos de contexto que definen eventos incrementadores pueden tener el valor a incrementar:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe se reserva el espacio de nombres `a.`. Aparte de esta restricción, las variables de datos de contexto solo tienen que ser únicas en su empresa de inicio de sesión para evitar conflictos.

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Para establecer *`products`* en el SDK móvil, debe utilizar una sintaxis especial. Para obtener más información, consulte [Variable products](/help/universal-windows/analytics/products.md).

## (Optional) Enable offline tracking {#section_955B2A03EB854742BDFC4A0A3C287009}

To store hits when the device is offline, you can enable offline tracking in the [SDK methods](/help/universal-windows/c-configuration/methods.md) file. Preste especial atención a los requisitos de marca de hora descritos en la referencia del archivo de configuración antes de habilitar el seguimiento sin conexión.

## Geo-location and points of interest {#section_BAD34A8DD013454DB355121316BD7FD4}

La geolocalización le permite medir datos de ubicación (latitud/longitud) y puntos de interés predefinidos. Each `TrackLocation` call sends:

* Latitud/Longitud y puntos de interés (o POI, si es que se encuentra en un POI definido en el archivo de configuración `ADBMobileConfig.json`). 

   Estos valores se pasan a variables de soluciones móviles para la realización automática de informes.

* Distancia al centro y precisión, pasados como datos de contexto.

   Captura mediante una regla de procesamiento.

Para realizar el seguimiento de una ubicación:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Si el siguiente POI está definido en el archivo de configuración `ADBMobileConfig.json`:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

When the device location is determined to be within a 7000 meter radius of the defined point, an `a.loc.poi` context data variable with the value `San Francisco` is sent in with the `TrackLocation` hit. Se envía una variable de contexto `a.loc.dist` con la distancia en metros desde las coordenadas definidas.

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

## Timed actions {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

Las acciones temporizadas le permiten medir el tiempo dentro de la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo de sesión y el tiempo total (entre sesiones) que la acción tarda en completarse. Esto sirve para definir segmentos donde comparar tiempo de compra, nivel de paso, flujo de verificación, etc.

* Total de segundos en la aplicación entre inicio y final (entre sesiones)
* Total de segundos entre inicio y final (tiempo de reloj)

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
