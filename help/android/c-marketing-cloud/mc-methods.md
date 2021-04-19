---
description: Esta es una lista de métodos del servicio de Experience Cloud ID que proporciona la biblioteca Android.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Esta es una lista de métodos del servicio de Experience Cloud ID que proporciona la biblioteca Android.
seo-title: Métodos del servicio de ID de Adobe Experience Platform
solution: Experience Cloud,Analytics
title: Métodos del servicio de ID de Adobe Experience Platform
topic-fix: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
exl-id: 8eb98c3f-c6ef-4593-ad3a-f566f4d4b6a2
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 100%

---

# Métodos del servicio de ID de Adobe Experience Platform {#experience-cloud-id-service-methods}

Esta es una lista de métodos del servicio de Experience Cloud ID que proporciona la biblioteca Android.

Ahora mismo, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de ID de Adobe Experience Platform.

Los métodos tienen un prefijo de acuerdo con la solución. Por ejemplo, los métodos de Experience Cloud ID llevan el prefijo `visitor`. Para obtener más información, consulte [Configuración de Experience Cloud ID](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Adjunta datos de visitantes de Adobe a una cadena URL para su uso con la biblioteca JavaScript de Adobe. Debe tener el SDK de Mobile 4.12 o posterior para usar este método. Para obtener más información, consulte [Función Asistente de agregación de ID de visitante](https://docs.adobe.com/content/help/es-ES/id-service/using/id-service-api/methods/appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Este método puede provocar una llamada que bloquee la red. No realice esta llamada en subprocesos en los que el tiempo sea importante.

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
      >Este método puede provocar una llamada que bloquee la red, de modo que **no** debe utilizarse desde un subproceso de interfaz de usuario.

* **syncIdentifiers**

   Con el Experience Cloud ID, puede establecer ID de cliente adicionales que se pueden asociar a cada visitante. La API de visitante acepta varios ID de cliente para el mismo visitante, con un identificador de tipo de cliente para separar el ámbito de los distintos ID de cliente. Este método corresponde a `setCustomerIDs` en la biblioteca de JavaScript.

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

* **syncIdentifier**

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

* **getUrlVariablesAsync**

   Este método, introducido en la versión 4.16.0, devuelve una cadena formada correctamente que contiene variables de URL del servicio de ID de visitante. Para obtener más información sobre cómo se utiliza este método, consulte [Métodos del servicio de identidad de Adobe Experience Platform](/help/android/reference/hybrid-app.md).

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

## Métodos públicos {#section_8AC744B431A3438C9B45629CA3EA0F51}

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
