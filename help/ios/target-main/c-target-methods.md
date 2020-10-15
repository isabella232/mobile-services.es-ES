---
description: Esta es una lista de métodos de Adobe Target que proporciona la biblioteca iOS.
seo-description: Esta es una lista de métodos de Adobe Target que proporciona la biblioteca iOS.
seo-title: Métodos de Target de iOS para Adobe Mobile Services
solution: Experience Cloud,Analytics
title: Métodos de Target para iOS
topic: Developer and implementation
uuid: 692bcda1-02ba-4902-bd65-15888adf1952
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '656'
ht-degree: 100%

---


# Métodos de Target para iOS {#target-methods}

Esta es una lista de métodos de Adobe Target que proporciona la biblioteca iOS.

Ahora mismo, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de ID de Adobe Experience Platform. Los métodos tienen un prefijo que depende de la solución. Por ejemplo, los métodos de llevan el prefijo `target` target.

>[!TIP]
>
>Las métricas del ciclo vital se envían como parámetros a cada carga mbox. Para obtener más información, consulte [Métricas del ciclo vital](/help/ios/metrics.md). Si está enviando solicitudes de Target dentro del método `didFinishLaunching` delegado, agregue una llamada `[ADBMobile trackAction:data:]` o `[ADBMobile trackState:data:]` antes del código de implementación de Target. De este modo, las solicitudes de Target contendrán todos los datos del ciclo vital.

## Referencia de clase: ADBTargetLocationRequest

### Propiedades

```objective-c
NSString *name; 
NSString *defaultContent; 
NSMutableDictionary *parameters;
```

### Constantes de cadena

>[!TIP]
>
>Las siguientes constantes facilitan el establecimiento de claves para parámetros personalizados.

```iOS
NSString *const ADBTargetParameterOrderId; 
NSString *const ADBTargetParameterOrderTotal; 
NSString *const ADBTargetParameterProductPurchasedId; 
NSString *const ADBTargetParameterCategoryId; 
NSString *const ADBTargetParameterMbox3rdPartyId; 
NSString *const ADBTargetParameterMboxPageValue; 
NSString *const ADBTargetParameterMboxPc; 
NSString *const ADBTargetParameterMboxSessionId; 
NSString *const ADBTargetParameterMboxHost;
```

>[!IMPORTANT]
>
>* Si utiliza algún SDK **anterior** a la versión 4.14.0, consulte [Parámetros de entrada](https://developers.adobetarget.com/api/#input-parameters) para obtener información sobre las limitaciones de parámetros.
   >
   >
* Si utiliza algún SDK de la versión 4.14.0 **o posterior**, consulte [Parámetros de entrada en bloque](https://developers.adobetarget.com/api/#batch-input-parameters) para obtener información sobre las limitaciones de parámetros.


### Métodos

* **targetLoadRequest:&#x200B;callback**

   Envía una solicitud al servidor Target configurado y devuelve el valor de la cadena de la oferta generada en una de bloque `callback`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) targetLoadRequest:(ADBTargetLocationRequest *)request
                        callback:(void (^)(NSString *content))callback;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile targetLoadRequest:myRequest
                          callback:^(NSString *content) {
                            // do something with content
                          }];
      ```

* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:requestLocationParameters:callback:**

   Envía una solicitud al servidor Target configurado y devuelve el valor de la cadena de la oferta generada en una llamada de retorno de bloque.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                requestLocationParameters:(nullable NSDictionary *)requestLocationParameters
                                 callback:(nullable void (^)(NSString
                                 * __nullable content))callback;
      ```

   * Devuelve: N/A

   * Estos son los parámetros de este método:

      * **`name`**

         Nombre del mbox/ubicación de Target que quiere recuperar.

         * **Tipo:** NSString*
      * **`defaultContent`**

         Valor devuelto en la llamada de retorno si el servidor Target no está disponible, o si el usuario no cumple los requisitos para la campaña.

         * **Tipo:** NSString*
      * **`profileParameters`**

         Los valores de este diccionario irán al objeto “profileParameters” en la solicitud a Target.

         * **Tipo:** NSDictionary*
      * **`orderParameters`**

         Los valores de este diccionario irán al objeto “order” en la solicitud a Target.

         * **Tipo:** NSDictionary
      * **`mboxParameters`**

         Los valores de este diccionario irán al objeto “mboxParameters” en la solicitud a Target.

         * **Tipo:** NSDictionary*
      * **`requestLocationParameters`**

         Los valores de este diccionario irán al objeto “requestLocation” en la solicitud a Target.

         **Tipo:** NSDictionary*

      * **`callback`**

         Se llama a este método con el contenido de la oferta del servidor Target. Si el servidor Target no está disponible, o si el usuario no cumple los requisitos para la campaña, se devuelve defaultContent.
      **Tipo:** función

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"myHeroBanner"
                            defaultContent:@"defaultHeroBanner.png"
                        profileParameters:@{@"age":@"20-29"}
                          orderParameters:nil
                           mboxParameters:@{@"customParam":@"customValue"}
                requestLocationParameters:@{@"host":@"my.hostname.com"}
                                 callback:^(NSString *content){
                                   // do something with content
                                   myImageView.image = [UIImage imageNamed:content];
                                 }];
      ```

      Para obtener más información sobre la API de Target subyacente, consulte [Desarrolladores de Adobe Target](https://docs.adobe.com/dev/products/target/reference/delivery.html).







* **targetLoadRequestWithName:defaultContent:profileParameters:orderParameters:mboxParameters:callback**

   Envía una solicitud al servidor de Target configurado y devuelve el valor de la cadena de la oferta generada en una llamada de retorno de bloque.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) targetLoadRequestWithName:(nullable NSString *)name
                          defaultContent:(nullable NSString *)defaultContent
                      profileParameters:(nullable NSDictionary *)profileParameters
                        orderParameters:(nullable NSDictionary *)orderParameters
                         mboxParameters:(nullable NSDictionary *)mboxParameters
                               callback:(nullable void (^)(NSString * __nullable content))callback;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile targetLoadRequestWithName:@"mboxName"
                            defaultContent:@"defaultContent"
                         profileParameters:{@"profile-parameter-key": @"profile-parameter-value"}
                           orderParameters:@{@"order-parameter-key": @"order-parameter-value"}
                            mboxParameters:@{@"mbox-parameter-key": @"mbox-parameter-value"}
                                   callback:^(NSString * content) {
                                           //do something with content 
                                 }
                               }];
      ```

* **targetCreateOrder&#x200B;ConfirmRequestWithName:&#x200B;orderId:&#x200B;orderTotal:&#x200B;productPurchasedId:&#x200B;parameters**

   Crea un `ADBTargetLocationRequest`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateOrderConfirmRequestWithName:(NSString *)name
                                      orderId:(NSString *)orderId
                                  orderTotal:(NSString *)orderTotal
                          productPurchasedId:(NSString *)productPurchasedId
                              parameters:(NSDictionary *)parameters;
      ```

* **targetCreateRequestWithName:&#x200B;&#x200B;defaultContent:&#x200B;parameters**

   Constructor de conveniencia para crear un objeto ADBTargetLocationRequest con los parámetros determinados.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (ADBTargetLocationRequest *)
      targetCreateRequestWithName:(NSString *)name
                           defaultContent:(NSString *)defaultContent
                               parameters:(NSDictionary *)parameters;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      ADBTargetLocationRequest *myRequest =  
      [ADBMobile targetCreateRequestWithName:@"heroBanner"
                              defaultContent:@"default.png"
                                  parameters:nil];
      ```

* **targetThirdPartyID**

   Devuelve el ID de terceros.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (nullable NSString *) targetThirdPartyID;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *thirdPartyId = [ADBMobile targetThirdPartyID];
      ```

* **targetSetThirdPartyID**

   Establece el ID de terceros.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) targetSetThirdPartyID:(nullable NSString *)thirdPartyID;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile targetSetThirdPartyID:@"thirdPartyID"];
      ```

* **targetClearCookies**

   Borra cualquier cookie objetivo de la aplicación.

   >[!TIP]
   >
   >Desde la versión 4.10.0 del SDK, Target ya no utiliza cookies. Este método restablece thirdPartyID y sessionID.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) targetClearCookies;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile targetClearCookies];
      ```

* **targetPcID**

   Devuelve el valor de PcID.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *myTargetPcID = [ADBMobile targetPcID];
      ```

* **targetSessionID**

   Devuelve el valor de SessionID.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (nullable NSString *) targetPcID;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *myTargetSessionID = [ADBMobile targetSessionID];
      ```

### Ejemplo

```objective-c
// make your request 
ADBTargetLocationRequest *myRequest =  
 [ADBMobile targetCreateRequestWithName:@"heroBanner"  
                         defaultContent:@"default.png"  
                          parameters:nil]; 
// load your request 
[ADBMobile targetLoadRequest:myRequest  
                    callback:^(NSString *content) { 
                        // do something with content 
                        heroImage.image = [UIImage imageNamed:content];
                    }];
```
