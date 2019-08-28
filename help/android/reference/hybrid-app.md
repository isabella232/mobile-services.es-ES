---
description: Si su aplicación abre contenido de una web móvil, asegúrese de que los visitantes no se identifiquen separadamente al moverlos entre la web nativa y la web móvil.
seo-description: Si su aplicación abre contenido de una web móvil, asegúrese de que los visitantes no se identifiquen separadamente al moverlos entre la web nativa y la web móvil.
seo-title: Seguimiento de visitantes entre una aplicación y una web móvil
solution: Marketing Cloud, Analytics
title: Seguimiento de visitantes entre una aplicación y una web móvil
topic: Desarrollador e implementación
uuid: 073572 e 4-4 c 55-4 b 27-b 4 a 7-e 4349 ccde 7 bf
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor tracking between an app and the mobile web {#visitor-tracking-between-an-app-and-mobile-web}

Si su aplicación abre contenido de una web móvil, asegúrese de que los visitantes no se identifiquen separadamente al moverlos entre la web nativa y la web móvil.

## ID de visitante en aplicaciones

El SDK para Android genera un ID de visitante exclusivo cuando se instala una aplicación. Este ID se almacena en la memoria persistente del dispositivo móvil, se envía con cada visita y solo se elimina cuando el usuario desinstala la aplicación.

>[!TIP]
>
>Los ID de visitante de la aplicación persisten a través de actualizaciones.

## ID de visitante en la web móvil

Las implementaciones web móviles típicas utilizan las mismas bibliotecas `s_code.js` o `AppMeasurement.js` estándar de Analytics que se emplean en los sitios de escritorio. Las bibliotecas de JavaScript tienen sus propios métodos para generar ID de visitante exclusivos, lo que causa que se genere un ID de visitante distinto al abrir contenido de la web móvil desde la aplicación.

## Implementing visitor tracking between an app and the mobile web {#section_1755BCCFD42D456EB2319141030FDDFF}

Para utilizar el mismo identificador de visitante en la aplicación y la web móvil:

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto intellij IDEA o Eclipse* en [implementación y ciclo vital de Core](/help/android/getting-started/dev-qs.md).

1. Para adjuntar información de visitante a la URL que se está utilizando para abrir el visor web, llame a `visitorAppendToURL`:

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   Como alternativa, a partir de la versión 4.16.0 de SDK, puede llamar a `Visitor.getUrlVariablesAsync` y generar su propia URL:

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

Este código de servicio de ID en el dominio de destino extrae el MID de la URL, en lugar de enviar una solicitud a Adobe para obtener un nuevo ID. El código utiliza el valor MID transferido para realizar el seguimiento del visitante.

Al producirse visitas en el contenido de la web móvil, compruebe en cada visita si existe el parámetro `mid` y que su valor coincide con el del parámetro `mid` enviado por el código de la aplicación.

## Troubleshooting visitor tracking {#section_9B641F8569E34A089C52AA28EA4C891D}

### I do not see `Visitor.appendToURL`.

Compruebe que el SDK de Adobe empaquetado en la aplicación principal es la versión 4.12.0 o superior.

**No veo Adobe ID en mi URL.**

* Compruebe lo siguiente:
   * La cadena URL utilizada para abrir el visor web la generó `Visitor.appendToURL(urlString)`.
   * Los Adobe ID están codificados.
To ensure that the IDs that are appended to the URL that is being opened, verify that the `adobe_mc` query parameter appears in the URL.

### El `mid` en la aplicación no es idéntico al del visor web.

* Compruebe lo siguiente:

   * La cadena URL que se está utilizando para abrir el visor web la generó `Visitor.appendToURL(urlString)`).
   * La cadena URL contiene parámetros de Adobe.

      The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.
   * La versión de `VisitorAPI.js` es 1.7.0 o superior.

Si estos pasos no solucionan sus problemas, póngase en contacto con Adobe Experience Care.

>[!IMPORTANT]
>
>Para permitir que Adobe valide la implementación, debe compartir una aplicación de ejemplo y el sitio asociado.

