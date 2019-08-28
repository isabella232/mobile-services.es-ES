---
description: Lista de métodos de Target provistos por la biblioteca de la Plataforma universal de Windows.
seo-description: Lista de métodos de Target provistos por la biblioteca de la Plataforma universal de Windows.
seo-title: Métodos de Target
solution: Marketing Cloud, Analytics
title: Métodos de Target
topic: Desarrollador e implementación
uuid: 2 ad 5953 b -7850-446 a -8053-b 3715 b 86329 b
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Métodos de Target {#target-methods}

Lista de métodos de Target provistos por la biblioteca de la Plataforma universal de Windows.

Actualmente, el SDK ofrece compatibilidad con varias soluciones de Adobe Experience Cloud, incluidas Analytics, Target y Audience Manager.

[Las métricas del ciclo vital](/help/universal-windows/metrics.md) se envían como parámetros a cada carga de mbox.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## Referencia de clase: TargetLocationRequest

## Propiedades

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Constantes de cadena

Esta información le ayuda a definir claves para parámetros personalizados.

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **Loadrequest (winjs: Loadrequest)**

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **Createrequest (winjs: Createrequest)**

   Crea un objeto `TargetLocationRequest` con los parámetros dados.

   * Esta es la sintaxis para este método:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **Createorderconfirmrequest (winjs: Createorderconfirmrequest)**

   Crea un objeto `TargetLocationRequest` con los parámetros dados.

   * Esta es la sintaxis para este método:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **Clearcookies (winjs: Clearcookies)**

   Borra las cookies de Target para la aplicación en el dispositivo actual.

   * Esta es la sintaxis para este método:

      ```csharp
      static void ClearCookies();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **Getpcid (winjs: Getpcid)**

   Devuelve la cookie PC ID para el dispositivo actual.

   * Esta es la sintaxis para este método:

      ```csharp
      staticPlatform::String ^GetPcId();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **Getsessionid (winjs: Getsessionid)**

   Devuelve la cookie Session ID para el dispositivo actual.

   * Esta es la sintaxis para este método:

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * Este es un ejemplo de código para este método:

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```

