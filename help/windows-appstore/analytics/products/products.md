---
description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer products directamente en la llamada al servidor.
seo-description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer products directamente en la llamada al servidor.
seo-title: Variable products
solution: Experience Cloud,Analytics
title: Variable products
topic: Developer and implementation
uuid: 2057a564-06ae-4171-bbe7-0baffa71608b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 13%

---


# Variable Products {#products-variable}

La variable products no se puede establecer mediante reglas de procesamiento. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer products directamente en la llamada al servidor.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value using the syntax defined for the *`products`*:

```js
cdata["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

Por ejemplo:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
cdata["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99"; 
cdata["m.purchaseid"] = "1234567890"; 
cdata["m.purchase"] = "1"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("purchase", cdata); 
// trackState example: 
ADB.Analytics.trackState("Order Confirmation", cdata);
```

*`products`* se establece en la solicitud de imagen y las demás variables se establecen como datos de contexto. Todas las variables de datos de contexto deben asignarse mediante reglas de procesamiento:

![](assets/products-procrules.png)

No es necesario asignar la *`products`* variable mediante reglas de procesamiento, ya que el SDK la establece directamente en la solicitud de imagen.
