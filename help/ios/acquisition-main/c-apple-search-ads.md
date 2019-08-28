---
description: El SDK de Adobe aprovecha las API de Atribución de la aplicación Search Ads de Apple para permitir a desarrolladores y especialistas en marketing realizar un seguimiento y atribuir descargas de aplicaciones originadas en campañas de Search Ads en el App Store de Apple.
seo-description: El SDK de Adobe aprovecha las API de Atribución de la aplicación Search Ads de Apple para permitir a desarrolladores y especialistas en marketing realizar un seguimiento y atribuir descargas de aplicaciones originadas en campañas de Search Ads en el App Store de Apple.
seo-title: Search Ads de Apple
solution: Marketing Cloud, Analytics
title: Search Ads de Apple
topic: Desarrollador e implementación
uuid: 790080 e 8-067 e -4 bfd-a 169-0027 db 4 fdff 3
translation-type: tm+mt
source-git-commit: 9c6923d14d1a5f30e5873299def61b0734e52429

---


# Search Ads de Apple {#apple-search-ads}

El SDK de Adobe aprovecha las API de Atribución de la aplicación Search Ads de Apple para permitir a desarrolladores y especialistas en marketing realizar un seguimiento y atribuir descargas de aplicaciones originadas en campañas de Search Ads en el App Store de Apple. Para obtener más información acerca de campañas de Search Ads, consulte [Search Ads de Apple](https://searchads.apple.com).

## Ventajas {#section_CEA30C652AC8470784B8054E299B80FA}

Estas son algunas ventajas de utilizar los anuncios de Apple:

* Puede medir fácilmente la efectividad de las campañas de descarga de aplicaciones de Search Ads agregando unas pocas líneas de código a la aplicación.
* Los desarrolladores pueden acceder a la fecha y hora de la descarga, y a la palabra clave que propició la conversión.

## Implementación de Apple Ads {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Para implementar Apple Ads, debe tener la versión 4.13.2 o posterior del SDK para iOS.

Para habilitar su aplicación para la atribución de Search Ads:

1. Implemente la versión 4.13.2 o superior del SDK de Adobe.

   Para obtener más información, consulte [Implementación principal y ciclo vital](/help/ios/getting-started/dev-qs.md).

1. Agregue el marco iAd al archivo del proyecto Xcode de la aplicación.

## Realización de informes de atribución de Search Ads {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Los datos de atribución de Search Ads de Apple se proporcionan en el nombre de adquisición, la fuente y el valor de los términos.

   If attribution = `true`, all of the `iad-*` fields will be included in the lifecycle hit.

   Además, se asignarán los siguientes valores del diccionario “`iad`” a campos habituales de datos de contexto de adquisición:

   * " `iad-campaign-id`" --&gt; " `a.referrer.campaign.trackingcode`"
   * " `iad-campaign-name`" --&gt;" `a.referrer.campaign.name``"
   * " `iad-adgroup-id`" --&gt; " `a.referrer.campaign.content`"
   * " `iad-keyword`" --&gt; " `a.referrer.campaign.term`"
   Esta asignación pone los valores a disposición de la realización de informes estándar.

