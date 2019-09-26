---
description: La función de recuperación previa de Adobe Target usa los SDK de Mobile para iOS para recuperar contenido de ofertas el menor número de veces posible almacenando en caché las respuestas del servidor.
seo-description: La función de recuperación previa de Adobe Target usa los SDK de Mobile para iOS para recuperar contenido de ofertas el menor número de veces posible almacenando en caché las respuestas del servidor.
seo-title: Recuperar previamente contenido de ofertas en iOS
title: Recuperar previamente contenido de ofertas en iOS
uuid: fef58042-65e2-4579-b8f1-d21554d2af57
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Recuperar previamente contenido de ofertas en iOS {#prefetch-offer-content-in-ios}

La función de recuperación previa de Adobe Target usa los SDK de Mobile para iOS para recuperar contenido de ofertas el menor número de veces posible almacenando en caché las respuestas del servidor.

>[!IMPORTANT]
>
>La funcionalidad de recuperación previa en los SDK móviles para iOS no se admite en los tipos de actividad de segmentación automática, asignación automática y personalización automatizada de Adobe Target.

Este proceso reduce el tiempo de carga, evita múltiples llamadas de red y permite que se notifique a Adobe Target acerca de qué mbox visitó el usuario de una aplicación móvil. Todo el contenido se recuperará y almacenará en caché durante la llamada de recuperación previa, y se recuperará de la memoria caché para todas las llamadas futuras que incluyan este contenido para el nombre de mbox especificado.

El contenido de recuperación previa no persiste de un inicio a otro. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch Input Parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

En la versión 4.14 o posterior del SDK, si se especifica, el `environmentId``ADBMobileConfig.json` se selecciona del archivo al iniciar una llamada TnT mbox de lote v2. Si no se especifica un `environmentId` en este archivo, no se envía ningún parámetro de entorno en la llamada mbox de lote TNT y se entrega una oferta para el entorno predeterminado.

Por ejemplo:

```
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Prefetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

Estos son los métodos que puede utilizar para recuperar previamente en iOS:

* **targetPrefetchContent**

   Envía una solicitud de recuperación previa con una matriz de ubicaciones al servidor de Target configurado y devuelve el estado de la solicitud en la llamada de retorno proporcionada.

   * Esta es la sintaxis para este método:

      ```objective-c
      (void) targetPrefetchContent:(nonnull NSArray*)targetPrefetchObjectArray 
                     withProfileParameters:(nullable NSDictionary*)profileParameters 
                            callback:(nullable void(^)(BOOL success))callback;
      ```

   * Here are the parameters for this method:

      * **`targetPrefetchArray`**

         Matriz de `TargetPrefetchObjects` que contiene el nombre y el valor mboxParameters de cada ubicación de Target que debe recuperarse previamente.

      * **`profileParameters`**

         Contiene las claves y los valores de los parámetros de perfil que deben utilizarse con cada recuperación previa de ubicación en esta solicitud.

      * **`callback`**

         Se invoca al completar la recuperación previa. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **targetLoadRequests**

   Ejecuta una solicitud de lotes para varias ubicaciones de mbox que se especifiquen en la matriz de solicitudes. Cada objeto de la matriz contiene una función de llamada de retorno que se invocará cuando el contenido esté disponible para su ubicación de mbox determinada.

   >[!IMPORTANT]
   >
   >Si el contenido de las ubicaciones solicitadas ya está en la caché, se devolverá inmediatamente en la llamada de retorno proporcionada. En caso contrario, el SDK enviará una solicitud de red a los servidores de Target para recuperar el contenido.

   * Esta es la sintaxis para este método:

      ```objective-c
      (void)targetLoadRequests:(nonnullNSArray*)requests 
               withProfileParameters:(nullableNSDictionary*)profileParameters;
      ```

   * Estos son los parámetros de este método:

      * **`requests`**

         Matriz de `TargetRequestObjects` que contiene el nombre, el contenido predeterminado, los parámetros y la función de llamada de retorno por cada ubicación que deba recuperarse.

      * **`profileParameters`**

         Contiene las claves y los valores de los parámetros de perfil que deben utilizarse con cada recuperación previa de ubicación en esta solicitud.

* **targetPrefetchClearCache**

   Borra los datos que la recuperación previa de Target ha permitido almacenar en la memoria caché.

   * Esta es la sintaxis para este método:

      ```objective-c
      (void) targetPrefetchClearCache; 
      ```

   * No hay parámetros para este método.

* **targetRequestObjectWithName**

   Crea y devuelve una instancia de `TargetRequestObject` con los datos proporcionados.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(nullableADBTargetRequestObject*)targetRequestObjectWithName:(nonnullNSString*)name
      defaultContent:(nonnullNSString*)defaultContent
      mboxParameters:(nullableNSDictionary*)mboxParameters
      callback:(nullablevoid(^)(NSString*__nullablecontent))callback;
      ```

   * No hay parámetros para este método.

* **createTargetPrefetchObject**

   Crea y devuelve una instancia de `TargetPrefetchObject` con los datos proporcionados.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(nullable ADBTargetPrefetchObject *) targetPrefetchObjectWithName:(nonnullNSString *)name
      mboxParameters:(nullableNSDictionary *)mboxParameters;
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

Estas son las clases públicas que admiten la recuperación previa en iOS:

### Referencia de clase: TargetPreFetchObject

Encapsula el nombre de mbox y los parámetros que se utilizan para la recuperación previa de mbox.

* **`name`**

   Nombre de la ubicación o mbox que desea recuperar.

   * **Tipo:** NSString*

* **`mboxParameters`**

   Un diccionario opcional que contiene los pares de clave-valor de los parámetros de mbox.

   * **Tipo:** NSDictionary*

* **`orderParameters`**

   El diccionario que contiene los pares de clave-valor de los parámetros de order.

   * **Tipo:** NSDictionary*

* **`productParameters`**

   El diccionario que contiene los pares de clave-valor de los parámetros de product.

   * **Tipo:** NSDictionary*

### Referencia de clase: TargetRequestObject

Esta clase encapsula el nombre de mbox, el contenido predeterminado, los parámetros de mbox y la llamada de retorno utilizada para las solicitudes de ubicación de Target.

* **`name`**

   Nombre de la ubicación solicitada.

   * **Tipo:** NSString*

* **`mboxParameters`**

   El valor NSString que representa el nombre de la ubicación o el mbox que desea recuperar.

   * **Tipo:** NSString*

* **`defaultContent`**

   El contenido predeterminado que se devolverá si no se puede acceder a los servidores de Target.

   * **Tipo:** NSString*

* **`callback`**

   Cuando el lote solicita ubicaciones de Target, la llamada de retorno se invocará cuando el contenido esté disponible para esta ubicación.

   * **Tipo:** función

## Code sample {#section_BF7F49763D254371B4656E17953D520C}

Este es un ejemplo de cómo recuperar previamente contenido mediante los SDK para iOS:

```objective-c
/** 
 * Prefetch Content 
 */ 
  
    NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
    NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
    NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
  
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    // Creating Prefetch Objects 
    ADBTargetPrefetchObject *prefetch1 = [ADBMobile targetPrefetchObjectWithName:@"logo" mboxParameters:mboxParameters1]; 
    prefetch1.productParameters = productParameters1; 
    prefetch1.orderParameters = orderParameters1; 
  
    ADBTargetPrefetchObject *prefetch2 = [ADBMobile targetPrefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2]; 
    prefetch2.productParameters = productParameters2; 
    prefetch2.orderParameters = orderParameters2; 

    // Creating prefetch Array 
    NSArray *prefetchArray = @[prefetch1,prefetch2]; 
  
    // Creating Profile parameters 
    NSDictionary *profileParmeters = @{@"age":@"20-32"};

    // Target API Call 
    [ADBMobile targetPrefetchContent:prefetchArray withProfileParameters:profileParmeters callback:^(BOOL isSuccess){ 
       // do something with the Boolean result 
    }];
```

Este es un ejemplo del lote `loadRequest` mediante el uso de los SDK para iOS:

```objective-c
/** 
 * Batch loadRequest  
 */ 
  
   NSDictionary *mboxParameters1 = @{@"status":@"platinum"}; 
   NSDictionary *productParameters1 = @{@"id":@"24D3412", 
                                        @"categoryId":@"Books"}; 
   NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM", 
                                      @"total":@"344.30", 
                                      @"purchasedProductIds":@"34, 125, 99"};

    NSDictionary *mboxParameters2 = @{@"userType":@"Paid"}; 
    NSDictionary *productParameters2 = @{@"id":@"764334", 
                                         @"categoryId":@"Online"}; 
    NSArray *purchaseIDs = @[@"id1",@"id2"]; 
    NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa", 
                                       @"total":@"54.90", 
                                       @"purchasedProductIds":purchaseIDs};

    ADBTargetRequestObject *request1 = [ADBMobile targetRequestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
  
    request1.productParameters = productParameters1; 
    request1.orderParameters = orderParameters1;

    ADBTargetRequestObject *request2 = [ADBMobile targetRequestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){ 
        // do something with the received content 
    }]; 
    request2.productParameters = productParameters1; 
    request2.orderParameters = orderParameters1;

    // create request object array 
    NSArray *requestArray = @[request1,request2]; 
  
    // Call the API 
    [ADBMobile targetLoadRequests:requestArray withProfileParameters:profileParmeters];
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

* `purchasedProducts` acepta una matriz de cadenas.