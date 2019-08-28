---
description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK para iOS 4.x, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products directamente en la llamada del servidor.
seo-description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK para iOS 4.x, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products directamente en la llamada del servidor.
seo-title: Variable products
solution: Marketing Cloud, Analytics
title: Variable products
topic: Desarrollador e implementación
uuid: 6 ece 4 d 27-ef 86-435 c-a 6 f 7-bd 76 be 1 c 95 ca
translation-type: tm+mt
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Products variable {#products-variable}

La variable products no se puede establecer mediante reglas de procesamiento. En el SDK para iOS 4.x, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products directamente en la llamada del servidor.

To set the *`products`* variable, set a context data key to `"&&products"`, and set the value by using the syntax that is defined for the *`products`* variable:

```objective-c
[contextData setObject:@"Category;Product;Quantity;Price[,Category;Product;Quantity;Price]" forKey:@"&&products"];
```

Por ejemplo:

```objective-c
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
 
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@";Running Shoes;1;69.95,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData]; 
```

*`products`* se establece en la solicitud de imagen y las demás variables se establecen como datos de contexto. Todas las variables de datos de contexto deben asignarse mediante reglas de procesamiento:

![](assets/map-products.png)

No es necesario que asigne la variable *`products`* empleando reglas de procesamiento, ya que el SDK la establece directamente en la solicitud de imagen.
