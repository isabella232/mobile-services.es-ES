---
description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK para iOS 4.x, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products directamente en la llamada del servidor.
seo-description: La variable products no se puede establecer mediante reglas de procesamiento. En el SDK para iOS 4.x, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products directamente en la llamada del servidor.
seo-title: Variable products
solution: Experience Cloud,Analytics
title: Variable products
topic: Desarrollador e implementación
uuid: 6ece4d27-ef86-435c-a6f7-bd76be1c95ca
translation-type: ht
source-git-commit: 7aff336586058302046a728a0b1b0ce12660c1ba

---


# Variable Products {#products-variable}

La variable products no se puede establecer mediante reglas de procesamiento. En el SDK para iOS 4.x, debe utilizar una sintaxis especial en el parámetro de datos de contexto para establecer products directamente en la llamada del servidor.

Para establecer la variable *`products`*, establezca una clave de datos de contexto en `"&&products"` y el valor empleando la sintaxis definida para la variable *`products`*:

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
