---
description: Esta es una lista de métodos de Adobe Target que proporciona la biblioteca Android.
keywords: android;biblioteca;móvil;sdk
seo-description: Esta es una lista de métodos de Adobe Target que proporciona la biblioteca Android.
seo-title: Target methods for Android
solution: Marketing Cloud,Analytics
title: Target methods for Android
topic: Desarrollador e implementación
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Métodos de Target para Android{#target-methods}

Esta es una lista de métodos de Adobe Target que proporciona la biblioteca Android.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target, Audience Manager y el servicio de identidad de la plataforma de Adobe Experience Cloud. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `target`.

>[!TIP]
>
>[Las métricas del ciclo vital](/help/android/metrics.md) se envían como parámetros a cada carga mbox.

## Class reference : TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Propiedades:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Constantes de cadena**

>[!TIP]
>
>Las siguientes constantes facilitan el uso al definir claves para parámetros personalizados.

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* If you are using SDKs **before** version 4.14.0, see [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters) for parameters limitations.
   >
   >
* If you are using SDKs version 4.14.0 **or later**, see [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters) for parameters limitations.


* **loadRequest**

   Envía una solicitud al servidor Target configurado y devuelve el valor de la cadena de la oferta generada en una llamada de retorno de bloque.

   * Esta es la sintaxis para este método:

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   Envía una solicitud al servidor Target configurado y devuelve el valor de la cadena de la oferta generada en una llamada de retorno de bloque.

   * Esta es la sintaxis para este método:

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
          }
      });
      ```

* **loadRequest**

   Envía una solicitud al servidor Target configurado y devuelve el valor de la cadena de la oferta generada en una TargetCallback.

   * Esta es la sintaxis para este método:

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **Devuelve:** N/A

   * **Parámetros:**

      Estos son los parámetros de este método:

      * **name**

         Nombre del mbox/ubicación de Target que quiere recuperar.

         * **** Tipo: Cadena
      * **defaultContent**

         Valor devuelto en la llamada de retorno si el servidor Target no está disponible, o si el usuario no cumple los requisitos para la campaña.

         * **** Tipo: Cadena
      * **profileParameters**

         Los valores de este diccionario irán al objeto “profileParameters” en la solicitud a Target.

         * **** Tipo: Mapa `<String, Object>`
      * **orderParameters**

         Los valores de este diccionario irán al objeto “order” en la solicitud a Target.

         * **** Tipo: Mapa `<String, Object>`
      * **mboxParameters**

         Los valores de este diccionario irán en la solicitud a Target.

         * **** Tipo: Mapa `<String, Object>`
      * **requestLocationParameters**

         Los valores de este diccionario irán al objeto “requestLocation” en la solicitud a Target.

         * **** Tipo: Mapa `<String, Object>`
      * **callback**

         Se llama a este método con el contenido de la oferta del servidor Target. Si el servidor Target no está disponible, o si el usuario no cumple los requisitos para la campaña, se devuelve defaultContent.

         * **** Tipo: TargetCallback `<String>`
   * Este es un código de muestra para este método:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      Para obtener más información acerca de la API de Target subyacente, consulte [Delivery (Entrega)](https://docs.adobe.com/dev/products/target/reference/delivery.html) en la ayuda del Desarrollador de Target.








* **createOrder&#x200B;ConfirmRequest**

   Crea un objeto TargetLocationRequest con los parámetros dados.

   * Esta es la sintaxis para este método:

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   Crea un objeto TargetLocationRequest con los parámetros dados.

   * Esta es la sintaxis para este método:

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   Borra cualquier cookie objetivo de la aplicación.

   * Esta es la sintaxis para este método:

      ```java
      public static void clearCookies();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   Devuelve el valor de pcID.

   * Esta es la sintaxis para este método:

      ```java
      public static String getPcID();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   Devuelve el ID de sesión.

   * Esta es la sintaxis para este método:

      ```java
      public static String getSessionID();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   Establece el ID de terceros.

   * Esta es la sintaxis para este método:

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   Devuelve el ID de terceros.

   * Esta es la sintaxis para este método:

      ```java
      public static String getThirdPartyID();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
