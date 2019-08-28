---
description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer products directamente en la llamada del servidor.
seo-description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer products directamente en la llamada del servidor.
seo-title: Variable products
solution: Marketing Cloud, Analytics
title: Variable products
topic: Desarrollador e implementación
uuid: 2057 a 564-06 ae -4171-bbe 7-0 baffa 71608 b
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable{#products-variable}

La variable products no se puede establecer mediante reglas de procesamiento. En el SDK móvil, debe utilizar una sintaxis especial dentro del parámetro de datos de contexto para establecer products directamente en la llamada del servidor.

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

No es necesario asignar *`products`* la variable mediante reglas de procesamiento, ya que el SDK la establece directamente en la solicitud de imagen.
