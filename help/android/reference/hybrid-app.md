---
description: Si su aplicación abre contenido de una web móvil, asegúrese de que los visitantes no se identifiquen separadamente al moverlos entre la web nativa y la web móvil.
seo-description: Si su aplicación abre contenido de una web móvil, asegúrese de que los visitantes no se identifiquen separadamente al moverlos entre la web nativa y la web móvil.
seo-title: Seguimiento de visitantes entre una aplicación y la web móvil
solution: Experience Cloud,Analytics
title: Seguimiento de visitantes entre una aplicación y la web móvil
topic: Developer and implementation
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 85%

---


# Seguimiento de visitantes entre una aplicación y la web móvil {#visitor-tracking-between-an-app-and-mobile-web}

Si su aplicación abre contenido de una web móvil, asegúrese de que los visitantes no se identifiquen separadamente al moverlos entre la web nativa y la web móvil.

## ID de visitante en aplicaciones

El SDK para Android genera un ID de visitante único cuando se instala una aplicación. Este ID se almacena en la memoria persistente del dispositivo móvil, se envía con cada visita y se elimina solo cuando el usuario desinstala la aplicación.

>[!TIP]
>
>Los ID de visitante persisten al actualizar las aplicaciones.

## ID de visitante en la web móvil

Las implementaciones web móviles típicas utilizan las mismas bibliotecas `s_code.js` o `AppMeasurement.js` estándar de Analytics que se emplean en los sitios de escritorio. Las bibliotecas de JavaScript tienen sus propios métodos para generar ID de visitante exclusivos, lo que causa que se genere un ID de visitante distinto al abrir contenido de la web móvil desde la aplicación.

## implementar Seguimiento de visitantes entre una aplicación y la web móvil {#section_1755BCCFD42D456EB2319141030FDDFF}

Para utilizar el mismo identificador de visitante en la aplicación y la web móvil:

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

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

El código de servicio de ID del dominio de destino extrae el MID de la dirección URL en lugar de enviar una solicitud al Adobe para obtener un nuevo ID. El código utiliza el MID pasado para rastrear el visitante.

Al producirse visitas en el contenido de la web móvil, compruebe en cada visita si existe el parámetro `mid` y que su valor coincide con el del parámetro `mid` enviado por el código de la aplicación.

## Solución de problemas de seguimiento de visitantes {#section_9B641F8569E34A089C52AA28EA4C891D}

### No veo `Visitor.appendToURL`.

Compruebe que el SDK de Adobe empaquetado en la aplicación principal es la versión 4.12.0 o superior.

**No veo Adobe ID en mi URL.**

* Compruebe lo siguiente:
   * La cadena URL utilizada para abrir el visor web la generó `Visitor.appendToURL(urlString)`.
   * Los Adobe ID están codificados. 
Para garantizar que los identificadores se adjunten a la URL que se está abriendo, verifique que el parámetro de consulta `adobe_mc` aparezca en la URL.

### El `mid` en la aplicación no es idéntico al del visor web.

* Compruebe lo siguiente:

   * La cadena URL que se está utilizando para abrir el visor web la generó `Visitor.appendToURL(urlString)`.
   * La cadena URL contiene parámetros de Adobe.

      La cadena debería contener `adobe_mc="SAMPLE_ID_DATA"`, donde `"SAMPLE_ID_DATA"` contiene los ID generados en el SDK de Adobe Mobile.
   * La versión de `VisitorAPI.js` es 1.7.0 o superior.

Si estos pasos no solucionan sus problemas, póngase en contacto con Adobe Experience Care.

>[!IMPORTANT]
>
>Para permitir que Adobe valide la implementación, deberá compartir una aplicación de ejemplo y el sitio asociado.

