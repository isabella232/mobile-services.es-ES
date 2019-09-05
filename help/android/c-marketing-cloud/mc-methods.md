---
description: Esta es una lista de métodos del servicio de Experience Cloud ID que proporciona la biblioteca Android.
keywords: android; library; mobile; sdk
seo-description: Esta es una lista de métodos del servicio de Experience Cloud ID que proporciona la biblioteca Android.
seo-title: Métodos del servicio de identidad de Adobe Experience Platform
solution: Marketing Cloud, Analytics
title: Métodos del servicio de identidad de Adobe Experience Platform
topic: Desarrollador e implementación
uuid: c 5107 a 7 e -273 b -4 f 71-8738-4 c 603479 b 24 c
translation-type: tm+mt
source-git-commit: 8fc515a6e89044b9dac98b3f207c5f43b658a2ec

---


# Métodos del servicio de identidad de Adobe Experience Platform{#experience-cloud-id-service-methods}

Esta es una lista de métodos del servicio de Experience Cloud ID que proporciona la biblioteca Android.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud], incluidas Analytics, Target, Audience Manager y el servicio de identidad de Adobe Experience Platform.

Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `visitor`. For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Adjunta datos de visitantes de Adobe a una cadena URL para su uso con la biblioteca JavaScript de Adobe. Para utilizar este método, debe tener la versión 4.12 del SDK de Mobile o una posterior. Para obtener más información, consulte [Función Asistente de agregación de ID de visitante](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Este método puede provocar una llamada de red bloqueadora. No realice esta llamada en subprocesos en los que el tiempo sea importante.

   * Esta es la sintaxis para este método:

      ```java
      public static String appendToURL(final String URL) 
      ```

      Cadena URL necesaria a la que se adjunta la información del visitante.

   * Este es un ejemplo de código para este método:

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   Recupera el Experience Cloud ID desde el servicio de ID de visitante.

   * Esta es la sintaxis para este método:

      ```java
      public static String getMarketingCloudId(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >This method can cause a blocking network call and should **not** be called from a UI thread.

* **syncIdentifiers**

   Con el Experience Cloud ID, puede configurar ID de cliente adicionales para asociarlos a cada visitante. La API de visitante acepta varios identificadores de cliente para el mismo visitante, con un identificador de tipo de cliente para separar el ámbito de los distintos identificadores de cliente. Este método corresponde a `setCustomerIDs` en la biblioteca de JavaScript.

   * Esta es la sintaxis para este método:

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **Syncidentifier**

   Sincroniza el tipo de identificador y el valor proporcionados con el servicio de ID de visitante.

   Pasa `authenticationState` como uno de los siguientes valores:

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Esta es la sintaxis para este método:

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   Sincroniza los identificadores proporcionados con el servicio de ID.

   Pasa `authenticationState` como uno de los siguientes valores:
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Esta es la sintaxis para este método:

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   Recupera una lista de objetos `ADBVisitorID` de solo lectura.

   * Esta es la sintaxis para este método:

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **Geturlvariablesasync**

   Este método, introducido en la versión 4.16.0, devuelve una cadena formada adecuadamente que contiene variables de URL del servicio de ID de visitante. Para obtener más información sobre cómo se utiliza este método, consulte [Métodos de servicio de identidad de Adobe Experience Platform](/help/android/reference/hybrid-app.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Public methods {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
