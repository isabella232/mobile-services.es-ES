---
description: Este es un ejemplo de la variable products con eVars de merchandising y events (eventos) específicos de productos.
seo-description: Este es un ejemplo de la variable products con eVars de merchandising y events (eventos) específicos de productos.
seo-title: Variable products con eVars de merchandising y events (eventos) específicos de productos
solution: Marketing Cloud,Analytics
title: Variable products con eVars de merchandising y events (eventos) específicos de productos
topic: Desarrollador e implementación
uuid: f913211e-97ad-4237-bfe4-7ded01295caf
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Products variable with merchandising eVars and product-specific events {#products-variable-with-merchandising-evars-and-product-specific-events}

Este es un ejemplo de la variable products con eVars de merchandising y events (eventos) específicos de productos.

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
>If you trigger a product-specific event by using the  variable, you must also set that event in the  variable. *`&&products`**`&&events`* Si no lo hace, el evento queda fuera del filtro durante el procesamiento.

