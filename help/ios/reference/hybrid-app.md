---
description: Si su aplicación abre contenido de una web móvil, debe asegurarse de que los visitantes no se identifiquen separadamente al moverlos entre la web nativa y la web móvil.
solution: Experience Cloud Services,Analytics
title: Seguimiento de visitantes entre una aplicación y la web móvil
topic-fix: Developer and implementation
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
exl-id: d8459d59-0edd-42c4-81b5-529b250accb4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 100%

---

# Seguimiento de visitantes entre una aplicación y la web móvil  {#visitor-tracking-between-an-app-and-mobile-web}

Si su aplicación abre contenido de una web móvil, debe asegurarse de que los visitantes no se identifiquen separadamente al moverlos entre la web nativa y la web móvil.

## ID de visitante en aplicaciones

El SDK de iOS genera un ID único de visitante cuando se instala una aplicación. Este ID se almacena en la memoria persistente del dispositivo móvil y se envía con cada visita. Solo se elimina cuando el usuario desinstala la aplicación.

>[!TIP]
>
>Los ID de visitante persisten al actualizar las aplicaciones.

## ID de visitante en la web móvil

Las implementaciones web móviles típicas utilizan las mismas bibliotecas `s_code.js` o `AppMeasurement.js` estándar de Analytics que se emplean en los sitios de escritorio. Las bibliotecas de JavaScript tienen sus propios métodos para generar ID únicos de visitantes, lo que causa que se genere un ID de visitante distinto al abrir contenido de la web móvil desde la aplicación.

Para utilizar el mismo ID de visitante en la aplicación y en la web móvil, pase el ID de visitante de la aplicación a la web móvil en la dirección URL:

## Implementar Seguimiento de visitantes entre una aplicación y la web móvil {#section_EDC91D6C67AD43999227707C2769C65D}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto* en [Implementación principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Para adjuntar información de visitante a la URL que se está utilizando para abrir el visor web, llame a `visitorAppendToURL`:

   ```objective-c
   NSURL *url = [NSURL URLWithString:@"https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   Como alternativa, a partir de la versión 4.16.0 de SDK, puede llamar a `visitorGetUrlVariablesAsync:` y generar su propia URL:

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

Este código de servicio de ID en el dominio de destino extrae el MID de la URL, en lugar de enviar una solicitud a Adobe para obtener el nuevo ID del visitante en cuestión. El código de servicio de ID en la página de destino emplea el MID transferido para hacer un seguimiento del visitante.

Al producirse visitas en el contenido de la web móvil, compruebe en cada visita si el parámetro `mid` está presente y que su valor coincida con el del parámetro `mid` enviado por el código de la aplicación.

## Solución de problemas de seguimiento de visitantes {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### No veo `[ADBMobile visitorAppendToURL:]`.

Compruebe que el SDK de Adobe empaquetado en la aplicación principal es la versión 4.12.0 o superior.

### No veo Adobe ID en mi URL.

Compruebe lo siguiente:

* La cadena URL que se está utilizando para abrir el visor web la generó  `[ADBMobile visitorAppendToURL:]`

* Los Adobe ID están codificados.

   Para comprobar que los ID están adjuntos a la URL que se está abriendo, busque el parámetro de consulta To ensure IDs that are appended to the URL that is being opened, compruebe que el parámetro de consulta `adobe_mc` se muestre en la URL.

### El “mid” en la aplicación no es idéntico al del visor web.*

Compruebe lo siguiente:

* La cadena URL que se está utilizando para abrir el visor web la generó `[ADBMobile visitorAppendToURL:]`

   La cadena URL contiene parámetros de Adobe.

   La cadena debería contener `adobe_mc="SAMPLE_ID_DATA"`, donde `"SAMPLE_ID_DATA"` contiene los ID generados en el SDK de Adobe Mobile.

* La versión de `VisitorAPI.js` es 1.7.0 o superior.

Si estos pasos no resuelven los problemas, póngase en contacto con Adobe Client Care; esté preparado para compartir una aplicación de ejemplo y el sitio asociado, de modo que Adobe pueda validar la implementación.
