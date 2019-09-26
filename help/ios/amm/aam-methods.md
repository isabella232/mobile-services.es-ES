---
description: Esta es una lista de métodos de Audience Manager que proporciona la biblioteca iOS.
seo-description: Esta es una lista de métodos de Audience Manager que proporciona la biblioteca iOS.
seo-title: Métodos de Audience Manager
solution: Marketing Cloud,Analytics
title: Métodos de Audience Manager
topic: Desarrollador e implementación
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods {#audience-manager-methods}

Esta es una lista de métodos de Audience Manager que proporciona la biblioteca iOS.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de identidad de la plataforma de Adobe Experience Cloud. Los métodos tienen un prefijo que depende de la solución y los de Manager llevan el prefijo “`audience`audience”.

Si Audience Manager está configurado en su archivo JSON, junto a `application:didFinishLaunchingWithOptions:` : se envía una señal que contiene métricas del ciclo vital.

* **audienceVisitorProfile**

   Devuelve el perfil del visitante que se obtuvo más recientemente. Si no se ha enviado ninguna señal, devuelve el valor `null`. El perfil del visitante está guardado en `NSUserDefaults` para acceder fácilmente entre los distintos lanzamientos de la aplicación.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * Este es el ejemplo de código para este menú:

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid**

   Devuelve el DPID actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   Devuelve el DPUUID actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   Establece el DPID y el DPUUID. Cuando se establece, ambos se adjuntan a cada señal.

   * El **ID del proveedor de datos (DPID)** es el ID del asociado de datos asignado por Audience Manager.
   * El **ID de usuario exclusivo del proveedor de datos (DPUUID)** es el ID exclusivo del proveedor de datos para el usuario.

      >[!IMPORTANT]
      >
      >Antes de la versión 4.13.x, DPUUID no se codificaba automáticamente. Desde la versión 4.13.x, el SDK primero descodifica el valor pasado y posteriormente vuelve a codificarlo. Este proceso garantiza que el SDK no anule la compatibilidad con versiones anteriores.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   Restaura el UUID de Audience Manager y purga el perfil del visitante actual.

   * Esta es la sintaxis para este método:

      ```objective-c
      +(void) audienceReset;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   Envía a la gestión de público una señal con características y obtiene una devolución de los segmentos coincidentes en una llamada de retorno a block.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## Ejemplo

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```
