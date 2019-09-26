---
description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products en la llamada del servidor.
keywords: android;library;mobile;sdk
seo-description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products en la llamada del servidor.
seo-title: Variable products
solution: Marketing Cloud,Analytics
title: Variable products
topic: Desarrollador e implementación
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

La variable products no se puede establecer mediante reglas de procesamiento. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products en la llamada del servidor.

To set the *products* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *products* variable:

```java
cdata.put("&&products", "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]");
```

Por ejemplo:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata.put("&&products", ";Running Shoes;1;69.95,;Running Socks;10;29.99"); 
cdata.put("myapp.purchase", "1"); 
cdata.put("myapp.purchaseid", "1234567890"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("purchase", cdata); 
// trackState example: 
Analytics.trackState("Order Confirmation", cdata);
```

The *products* variable is set on the image request, and the other variables are set as context data. Todas las variables de datos de contexto deben asignarse mediante reglas de procesamiento:

![](assets/map-products.png)

No es necesario que asigne la variable *products* variable by using processing rules because this variable is set directly on the image request by the SDK.
