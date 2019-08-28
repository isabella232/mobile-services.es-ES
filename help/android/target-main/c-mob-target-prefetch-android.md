---
description: La función de recuperación previa de Adobe Target usa los SDK de Mobile para Android y permite almacenar en caché las respuestas del servidor para recuperar contenido de ofertas el menor número posible de veces.
seo-description: La función de recuperación previa de Adobe Target usa los SDK de Mobile para Android y permite almacenar en caché las respuestas del servidor para recuperar contenido de ofertas el menor número posible de veces.
seo-title: Recuperación previa del contenido de ofertas en Android
title: Recuperación previa del contenido de ofertas en Android
uuid: 063451 b 8-e 191-4 d 58-8 ed 8-1723 e 310 ad 1 a
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Recuperación previa del contenido de ofertas en Android {#prefetch-offer-content-in-android}

La función de recuperación previa de Adobe Target usa los SDK de Mobile para Android y permite almacenar en caché las respuestas del servidor para recuperar contenido de ofertas el menor número posible de veces.

>[!IMPORTANT]
>
>La funcionalidad de recuperación previa en los SDK móviles para Android no es compatible con los tipos de actividades de Segmentación automática, Asignación automática y Personalización automatizada en Adobe Target.

Este proceso reduce el tiempo de carga, evita múltiples llamadas de red y permite que se notifique a Adobe Target acerca de qué mbox visitó el usuario de una aplicación móvil. Todo el contenido se recuperará y almacenará en caché durante la llamada de recuperación previa, y se recuperará de la memoria caché para todas las llamadas futuras que incluyan este contenido para el nombre de mbox especificado.

El contenido de recuperación previa no persiste de un inicio a otro. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

En la versión 4.14 o posterior del SDK, si se especifica, el `environmentId``ADBMobileConfig.json` se selecciona del archivo al iniciar una llamada TnT mbox de lote v2. Si no se especifica un `environmentId` en este archivo, no se envía ningún parámetro de entorno en la llamada mbox de lote TNT y se entrega una oferta para el entorno predeterminado.

Por ejemplo:

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Pre-fetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

A continuación encontrará los métodos que puede utilizar para la recuperación previa en Android:

* **prefetchContent**

   Envía una solicitud de recuperación previa con una matriz de ubicaciones al servidor de Target configurado y devuelve el estado de la solicitud en la llamada de retorno proporcionada.

   * Esta es la sintaxis para este método:

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * Estos son los parámetros de este método:

      * **targetPrefetchArray**

         Matriz de `TargetPrefetchObjects` que contiene el nombre y el valor mboxParameters de cada ubicación de Target que debe recuperarse previamente.

      * **profileParameters**

         Contiene las claves y los valores de los parámetros de perfil que deben utilizarse con cada recuperación previa de ubicación en esta solicitud.

      * **callback**

         Se invoca al completar la recuperación previa. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **loadRequests**

   Ejecuta una solicitud de lotes para varias ubicaciones de mbox que se especifiquen en la matriz de solicitudes.  Cada objeto de la matriz contiene una función de llamada de retorno que se invocará cuando el contenido esté disponible para su ubicación de mbox determinada.

   >[!IMPORTANT]
   >
   >Si el contenido de las ubicaciones solicitadas ya se encuentra en caché, se devolverá inmediatamente en la llamada de retorno proporcionada. En caso contrario, el SDK enviará una solicitud de red a los servidores de Target para recuperar el contenido.

   * Esta es la sintaxis para este método:

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * Estos son los parámetros de este método:

      * **requestArray**

         Matriz de `TargetRequestObjects` que contiene el nombre, el contenido predeterminado, los parámetros y la función de llamada de retorno por cada ubicación que deba recuperarse.

      * **profileParameters**

         Contiene las claves y los valores de los parámetros de perfil que deben utilizarse con cada recuperación previa de ubicación en esta solicitud.

* **clearPrefetchCache**

   Borra los datos que la recuperación previa de Target ha permitido almacenar en la memoria caché.

   * Esta es la sintaxis para este método:

      ```java
      public static void clearPrefetchCache();
      ```

   * No existen parámetros para este método.

* **createTargetRequestObject**

   Crea y devuelve una instancia de `TargetRequestObject` con los datos proporcionados.

   * Esta es la sintaxis para este método:

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   Crea y devuelve una instancia de TargetPrefetchObject con los datos proporcionados.

   * Esta es la sintaxis para este método:

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

Estas son las clases públicas que admiten la recuperación previa en Android:

### Referencia de clase: Targetprefetchobject

Encapsula el nombre de mbox y los parámetros que se utilizan para la recuperación previa de mbox.

* **`name`**

   Nombre de la ubicación que se recuperará previamente.
   * **Tipo**: String

* `mboxParameters`

   Colección de pares de clave-valor que se adjuntarán como `mboxParameters` para la solicitud de este `TargetPrefetchObject`.
   * **Tipo**: Mapa`<String, Object>`

* **`orderParameters`**

   Colección de pares de clave-valor que se adjuntarán al mbox actual bajo el nodo order.
   * **Tipo**: Mapa `<String, Object>`

* **`productParameters`**

   Colección de pares de clave-valor que se adjuntarán al mbox actual bajo el nodo product.

   * **Tipo**: Mapa `<String, Object>`


### Referencia de clase: Targetrequestobject

Esta clase encapsula el nombre de mbox, el contenido predeterminado, los parámetros de mbox y la llamada de retorno utilizada para las solicitudes de ubicación de Target.

* **`mboxName`**

   Nombre de la ubicación solicitada.

   * **Tipo**: String

* **`mboxParameters`**

   Colección de pares de clave-valor que se adjuntarán como `mboxParameters` para la solicitud de este  `TargetRequestObject`.

   * **Tipo: Mapa`<String, Object>`**

* **`orderParameters`**

   Colección de pares de clave-valor que se adjuntarán al mbox actual bajo el nodo order.

   * **Tipo**: Mapa `<String, Object>`

* **`productParameters`**

   Colección de pares de clave-valor que se adjuntarán al mbox actual bajo el nodo product.

   * **Tipo**: Mapa `<String, Object>`

* **`defaultContent`**

   Valor de cadena devuelto en la llamada de retorno si el SDK no puede recuperar contenido de los servidores de Target.

   * **Tipo**: String

* **`callback`**

   Puntero de función al que se llamará cuando el contenido del `TargetRequestObject` determinado esté disponible.

   * **Tipo**: Target. targetcallback`<String>`


## Code sample {#section_BF7F49763D254371B4656E17953D520C}

A continuación encontrará un ejemplo de cómo recuperar previamente contenido mediante los SDK para Android:

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
```

## Información adicional {#section_A454BAD1CD49423E86C71BAEE06125FD}

A continuación encontrará información adicional sobre estos ejemplos:

* `ProductParameters` solo permite las claves siguientes:

   * `id`
   * `categoryId`

* `OrderParameters` solo permite las claves siguientes:

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` acepta una ArrayList de cadenas.
