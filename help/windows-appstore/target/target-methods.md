---
description: Lista de los métodos de Destinatario proporcionados por la biblioteca Universal App Store para Windows 8.1.
seo-description: Lista de los métodos de Destinatario proporcionados por la biblioteca Universal App Store para Windows 8.1.
seo-title: Métodos de Target
solution: Experience Cloud,Analytics
title: Métodos de Target
topic: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 42%

---


# Métodos de Target {#target-methods}

Lista de los métodos de Destinatario proporcionados por la biblioteca Universal App Store para Windows 8.1.

Actualmente, el SDK admite varias soluciones de Adobe Experience Cloud, incluidas Analytics, Destinatario y Audience Manager. Los métodos tienen un prefijo que depende de la solución. Los métodos de Analytics llevan el prefijo &quot;Destinatario&quot;.

[Las métricas del ciclo vital](/help/windows-appstore/metrics.md) se envían como parámetros a cada carga mbox.

>[!TIP]
>
>Cuando se consumen `winmd` métodos de winJS (JavaScript), se reduce automáticamente la primera letra de todos los métodos.

## Referencia de clase: TargetLocationRequest

### Propiedades

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Constantes de cadena

Esta información le ayuda a establecer claves para los parámetros personalizados.

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

* **LoadRequest (winJS: loadRequest)**

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * Esta es la sintaxis para este método:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateRequest (winJS: createRequest)**

   Creates a `TargetLocationRequest` object with the given parameters.

   * Esta es la sintaxis para este método:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest (winJS: createOrder &#x200B; ConfirmRequest)**

   Creates a `TargetLocationRequest` object with the given parameters.

   * Esta es la sintaxis para este método:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies (winJS: clearCookies)**

   Borra las cookies de Destinatario para la aplicación en el dispositivo actual.

   * Esta es la sintaxis para este método:

      ```csharp
      static void ClearCookies(); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS: getPcId)**

   Devuelve la cookie de ID de PC del dispositivo actual.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Este es un ejemplo de código para este método:

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId (winJS: getSessionId)**

   Devuelve la cookie de ID de sesión del dispositivo actual.

   * Esta es la sintaxis para este método:

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Este es un ejemplo de código para este método:

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```

