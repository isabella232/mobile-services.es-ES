---
description: La variable de productos no se puede establecer mediante reglas de procesamiento. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer productos en la llamada al servidor.
keywords: android;library;mobile;sdk
seo-description: La variable de productos no se puede establecer mediante reglas de procesamiento. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer productos en la llamada al servidor.
seo-title: Variable products
solution: Experience Cloud,Analytics
title: Variable products
topic: Developer and implementation
uuid: f4484022-cb8b-4dea-9209-5a110ba607df
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '185'
ht-degree: 100%

---


# Variable Products {#products-variable}

La variable de productos no se puede establecer mediante reglas de procesamiento. En el SDK de Mobile, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer productos en la llamada al servidor.

Para establecer la variable *products*, establezca una clave de datos de contexto en `"&&products"` y el valor empleando la sintaxis definida para la variable *products*:

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

La variable *products* se establece en la solicitud de imagen y las demás variables se establecen como datos de contexto: Todas las variables de datos de contexto deben asignarse mediante reglas de procesamiento:

![](assets/map-products.png)

No es necesario que asigne la variable  *products* mediante reglas de procesamiento, ya que el SDK la establece directamente en la solicitud de imagen.
