---
description: El SDK de Adobe aprovecha las API de Atribución de la aplicación Search Ads de Apple para permitir a desarrolladores y especialistas en marketing realizar un seguimiento y atribuir descargas de aplicaciones originadas en campañas de Search Ads en el App Store de Apple.
seo-description: El SDK de Adobe aprovecha las API de Atribución de la aplicación Search Ads de Apple para permitir a desarrolladores y especialistas en marketing realizar un seguimiento y atribuir descargas de aplicaciones originadas en campañas de Search Ads en el App Store de Apple.
seo-title: Search Ads de Apple
solution: Experience Cloud,Analytics
title: Search Ads de Apple
topic: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 94%

---


# Search Ads de Apple {#apple-search-ads}

El SDK de Adobe aprovecha las API de Atribución de la aplicación Search Ads de Apple para permitir a desarrolladores y especialistas en marketing realizar un seguimiento y atribuir descargas de aplicaciones originadas en campañas de Search Ads en el App Store de Apple. Para obtener más información acerca de campañas de Search Ad, consulte [Search Ads de Apple](https://searchads.apple.com/es/).

## Ventajas {#section_CEA30C652AC8470784B8054E299B80FA}

Estas son algunas ventajas de utilizar los anuncios de Apple:

* Puede medir fácilmente la efectividad de las campañas de descarga de aplicaciones de Search Ads agregando unas pocas líneas de código a la aplicación.
* Los desarrolladores pueden acceder a la fecha y hora de la descarga, y a la palabra clave que propició la conversión.

## Implementación de Apple Ads {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Para implementar Apple Ads, debe tener la versión 4.13.2 o posterior del SDK para iOS.

Para habilitar su aplicación para la atribución de Search Ads:

1. Implementar el SDK de Adobe versión 4.13.2 o superior.

   For more information, see [Core implementation and lifecycle](/help/ios/getting-started/dev-qs.md).

1. Agregue el marco iAd al archivo del proyecto Xcode de la aplicación.

## Realización de informes de atribución de Search Ads {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Los datos de atribución de Search Ads de Apple se proporcionan en el nombre de adquisición, la fuente y el valor de los términos.

   Si atribución tiene el valor `true`, todos los campos `iad-*` se incluyen en la visita de ciclo vital.

   Además, se asignarán los siguientes valores del diccionario `"iad"` a campos habituales de datos de contexto de adquisición:

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --> `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --> `"a.referrer.campaign.content"`
   * `"iad-keyword"` --> `"a.referrer.campaign.term"`
   Esta asignación permite realizar informes estándar con los valores.
