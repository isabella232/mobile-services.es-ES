---
description: Estos son los métodos de servicio de identidad de Adobe Experience Platform que proporciona la biblioteca iOS.
seo-description: Estos son los métodos de servicio de identidad de Adobe Experience Platform que proporciona la biblioteca iOS.
seo-title: Métodos del servicio de identidad de Adobe Experience Platform
solution: Marketing Cloud, Analytics
title: Métodos del servicio de identidad de Adobe Experience Platform
topic: Desarrollador e implementación
uuid: cdd 307 bc -8 b 7 d -47 a 8-b 77 e -00902 b 9 e 2968
translation-type: tm+mt
source-git-commit: cbbb85b4d117fcaa502a1e01423f1f5d3b2ecc2b

---


# Métodos del servicio de identidad de Adobe Experience Platform {#experience-cloud-id-service-methods}

Estos son los métodos de servicio de identidad de Adobe Experience Platform que proporciona la biblioteca iOS.

Ahora mismo, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de ID de visitante de Experience Cloud.

Methods are prefixed according to the solution, and Experience Cloud ID methods are prefixed with `visitor`. Para obtener más información, consulte [Habilitar el Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).

* **`+`(nullable NSURL`*`) visitorappendtourl: (nullable NSURL`*`) url;**

   Adjunta datos de visitantes de Adobe a una cadena URL para su uso con la biblioteca JavaScript de Adobe. Para utilizar este método, debe tener la versión 4.12 o superior del SDK móvil. Para obtener más información, consulte [Función Asistente de agregación de ID de visitante](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Este método puede provocar una llamada de red bloqueadora. No realice esta llamada en subprocesos en los que el tiempo sea importante.

   * Input: `URL<NSURL>`
A required URL string that the visitor information will be appended to.
   * `URL<NSURL>`
Cadena con la información del visitante adjunta.

   * Este es un ejemplo de código para este método:

      ```objective-c
       NSURL *url = [NSURL URLWithString:@"https://www.example.com"];  
       NSURL *decoratedURL = [ADBMobile visitorAppendToURL: url];  
       [[UIApplication sharedApplication] openURL: decoratedURL];  
      ```

* **visitorMarketingCloudID**

   Recupera el Experience Cloud ID desde el servicio de ID.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (NSString  *)  visitorMarketingCloudID;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSString *mcid = [ADBMobile visitorMarketingCloudID]; 
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **visitorSyncIdentifiers:**

   Con el Experience Cloud ID, puede configurar ID de cliente adicionales para asociarlos a cada visitante. La API de visitante acepta varios ID de cliente para el mismo visitante, con un identificador de tipo de cliente para separar el ámbito de los distintos ID de cliente. Este método corresponde a `setCustomerIDs` en la biblioteca de JavaScript.

   * Esta es la sintaxis para este método:

      ```objective-c
      +  (void)  visitorSyncIdentifiers:(NSDictionary  *)identifiers;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"idType":@"idValue"}];
      ```

* **visitorSyncIdentifiers:authenticationState:**

   Sincroniza los identificadores proporcionados con el servicio de ID. Pasa `authState` como uno de los siguientes valores:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Esta es la sintaxis para este método:

      ```objective-c
      +  (void) visitorSyncIdentifiers:(nullable NSDictionary  *)identifiers  authenticationState:(ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile visitorSyncIdentifiers:@{@"myIdType":@"valueForUser"}  authenticationState:ADBMobileVisitorAuthenticationStateAuthenticated]; 
      ```

* **visitorSyncIdentifierWithType:identifier:authenticationState:**

   Sincroniza el tipo de identificador y el valor proporcionados con el servicio de ID. Pass in the `authState` one of the following values:

   * `ADBMobileVisitorAuthenticationStateUnknown`
   * `ADBMobileVisitorAuthenticationStateAuthenticated`
   * `ADBMobileVisitorAuthenticationStateLoggedOut`

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void) visitorSyncIdentifierWithType:(nullable NSString *)identifierType  
      identifier:(nullable NSString *)identifier authenticationState:
      (ADBMobileVisitorAuthenticationState)authState; 
      ```

   * Esta es la sintaxis para este método:

      ```objective-c
      [ADBMobile visitorSyncIdentifierWithType:@"myIdType" identifier:@"valueForUser"  
      authenticationState:ADBMobileVisitorAuthenticationStateLoggedOut]; 
      ```

* **visitorGetIDs**

   Recupera una matriz de objetos `ADBVisitorID` de solo lectura.

   * Esta es la sintaxis para este método:

      ```objective-c
      +  (nullable NSArray *) visitorGetIDs;
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      NSArray *myVisitorIDs = [ADBMobile visitorGetIDs];
      ```

* **Visitorgeturlvariablesasync**

   Este método, introducido en la versión 4.16.0, devuelve una cadena formada adecuadamente que contiene variables de URL del servicio de ID de visitante. Para obtener más información sobre cómo se utiliza este método, consulte [Métodos de servicio de identidad de Adobe Experience Platform](/help/ios/reference/hybrid-app.md).

   * Esta es la sintaxis para este método:

      ```objectivec
      + (void) visitorGetUrlVariablesAsync:(nullable void (^)(NSString* __nullable urlVariables))callback;
      ```

   * Este es un ejemplo de código para este método:

      ```objectivec
      NSString *urlString = @"https://www.mydomain.com/index.php"; 
      [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
        NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
        // use urlStringWithVisitorData 
      }];
      ```

## Interfaz ADBVisitorID {#section_2FF74454D25C4ADABAC5E43CBFAAEC26}

**Métodos públicos:**

```objective-c
- (nullable NSString *) idType; 
- (nullable NSString *) identifier; 
- (ADBMobileVisitorAuthenticationState) authenticationState; 
```

## ADBMobileVisitorAuthenticationState enum {#section_A55A3F336DDF4F838900632087F51430}

```objective-c
ADBMobileVisitorAuthenticationStateUnknown, 
ADBMobileVisitorAuthenticationStateAuthenticated, 
ADBMobileVisitorAuthenticationStateLoggedOut
```

