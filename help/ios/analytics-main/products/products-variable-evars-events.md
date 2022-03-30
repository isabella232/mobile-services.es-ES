---
description: Este es un ejemplo de la variable products con eVars de comercialización y eventos específicos de productos.
solution: Experience Cloud Services,Analytics
title: Variable products con eVars de comercialización y eventos específicos de productos
topic-fix: Developer and implementation
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
exl-id: f438190d-0d2d-4bcd-a1c7-156e46e61162
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 100%

---

# Variable products con eVars de comercialización y eventos específicos de productos {#products-variable-with-merchandising-evars-and-product-specific-events}

Este es un ejemplo de la variable products con eVars de comercialización y eventos específicos de productos.

```
//create a context data dictionary 
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
  
// add products, a purchase id, a purchase context data key, and any other data you want to collect. 
// Note the special syntax for products 
[contextData setObject:@"event1" forKey:@"&&events"]; 
[contextData setObject:@";Running Shoes;1;69.95;event1=5.5;eVar1=Merchandising,;Running Socks;10;29.99" forKey:@"&&products"]; 
[contextData setObject:@"1234567890" forKey:@"m.purchaseid"]; 
[contextData setObject:@"1" forKey:@"m.purchase"]; 
  
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
[ADBMobile trackAction:@"purchase" data:contextData]; 
// trackState example: 
[ADBMobile trackState:@"Order Confirmation" data:contextData];
```

>[!TIP]
>
>Si activa un evento específico de producto mediante la variable *`&&products`*, también debe configurar ese evento en la variable *`&&events`*. Si no lo hace, el evento queda fuera del filtro durante el procesamiento.
