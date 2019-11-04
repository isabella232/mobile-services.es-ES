---
description: Las acciones son los eventos que tienen lugar en su aplicación y que desea medir. Cada acción tiene una o más métricas correspondientes que se incrementan cada vez que tiene lugar el evento. Por ejemplo, puede realizar un seguimiento de cuándo se realiza una nueva suscripción, cuándo se ve un artículo o cuándo se completa un nivel. Las métricas correspondientes a estos eventos se configuran como suscripciones, artículos leídos y niveles completados.
seo-description: Las acciones son los eventos que tienen lugar en su aplicación y que desea medir. Cada acción tiene una o más métricas correspondientes que se incrementan cada vez que tiene lugar el evento. Por ejemplo, puede realizar un seguimiento de cuándo se realiza una nueva suscripción, cuándo se ve un artículo o cuándo se completa un nivel. Las métricas correspondientes a estos eventos se configuran como suscripciones, artículos leídos y niveles completados.
seo-title: Seguimiento de acciones de aplicaciones
solution: Experience Cloud,Analytics
title: Seguimiento de acciones de aplicaciones
topic: Desarrollador e implementación
uuid: 62017be1-5395-4d16-bde3-4c40a2c012d4
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Seguimiento de acciones de aplicaciones {#track-app-actions}

Las acciones son los eventos que tienen lugar en su aplicación y que desea medir. Cada acción tiene una o más métricas correspondientes que se incrementan cada vez que tiene lugar el evento. Por ejemplo, puede realizar un seguimiento de cuándo se realiza una nueva suscripción, cuándo se ve un artículo o cuándo se completa un nivel. Las métricas correspondientes a estos eventos se configuran como suscripciones, artículos leídos y niveles completados.

No se realiza un seguimiento automático de las acciones y, por lo tanto, para realizar un seguimiento de un evento, debe llamar a `trackAction`.

## Seguimiento de acciones {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Cuando la acción de la que desea realizar un seguimiento se produzca en la aplicación, llame a `trackAction` para enviar una visita para esta acción.

   ```objective-c
   [ADBMobile trackAction:@"myapp.ActionName"  
                     data:nil];
   ```

   >[!TIP]
   >
   >Si el código donde quiere agregar esta llamada pudiera estar ejecutándose mientras la aplicación se encuentra en segundo plano, llame a `trackActionFromBackground` en lugar de a `trackAction`.

1. En la interfaz de usuario de Adobe Mobile Services, seleccione su aplicación y haga clic en **[!UICONTROL Administrar configuración de la aplicación]**.

1. Haga clic en **[!UICONTROL Administrar variables y métricas]** y, después, haga clic en la pestaña **[!UICONTROL Métricas personalizadas]**.

1. Asigne el nombre de datos de contexto definido en su código, por ejemplo, `a.action=myapp.ActionName`, a un evento personalizado.

   ![](assets/map-event-context-data.png)

También puede establecer una propiedad que contenga todos los valores de acción asignando una propiedad personalizada con un nombre como **[!UICONTROL Acciones personalizadas]** y estableciendo su valor en `a.action`.

![](assets/map-custom-prop.png)

## Envío de datos adicionales {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además del nombre de acción, puede enviar datos de contexto adicionales con cada llamada de seguimiento de acción:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

El valor de los datos de contexto debe asignarse a variables personalizadas:

![](assets/map-variable-context-action.png)

## Seguimiento de acciones en segundo plano {#section_AC13013F207D4FBAAF27E4412034251E}

Si realiza el seguimiento de una acción cuyo código podría estar ejecutándose mientras la aplicación se encuentra en segundo plano, utilice `trackActionFromBackground` en lugar de `trackAction`. Aunque `trackActionFromBackground` contiene lógica adicional para impedir que las llamadas al ciclo vital se activen cuando no deben, los parámetros son los mismos.

## Informes de acción {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Interfaz | Informe |
|--- |--- |
| Adobe Mobile Services | **** Informe de rutas de acción. Vea el orden en el que ocurren las acciones en su aplicación. También puede hacer clic en **[!UICONTROL Personalizar]** en cualquier informe para ver las acciones clasificadas, organizadas por tendencias o en un informe desglosado. O puede aplicar un filtro para ver acciones de un segmento específico. |
| Informes y análisis de marketing | **[!UICONTROL Informe Evento personalizado]**. Una vez que una acción está asignada a un evento personalizado, puede ver eventos móviles similares a todos los demás eventos de Analytics. |
| Análisis específico | **[!UICONTROL Informe Evento personalizado]**. Una vez que una acción está asignada a un evento personalizado, puede ver eventos móviles similares a todos los demás eventos de Analytics. |