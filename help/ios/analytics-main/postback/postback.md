---
description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Al aprovechar los mismos activadores y características que se utilizan para mostrar un mensaje en la aplicación, puede configurar el SDK para que envíe datos personalizados a un destino de terceros.
seo-description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Al aprovechar los mismos activadores y características que se utilizan para mostrar un mensaje en la aplicación, puede configurar el SDK para que envíe datos personalizados a un destino de terceros.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Información general de Postbacks
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 27%

---


# Información general de Postbacks {#postbacks}

Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Al aprovechar los mismos activadores y características que se utilizan para mostrar un mensaje en la aplicación, puede configurar el SDK para que envíe datos personalizados a un destino de terceros.

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.6.0 o posterior del SDK.

Los mensajes postback se ponen en cola y siguen todas las reglas en línea y sin conexión existentes que rigen la recopilación de datos de análisis. Cuando un mensaje coincide (como hacen los mensajes mostrados), los mensajes postback no cancelan el resto de los mensajes. Esto permite que se produzcan varios postbacks en la misma visita de análisis. Para ver la definición, consulte la fila *postbacks* en [Configuración JSON de ADBMobile](/help/ios/configuration/json-config/json-config.md).

## Expansiones de plantilla {#section_6758AD05A24C4E9E965F5253294C164A}

Las expansiones de plantilla están disponibles en las propiedades `templateurl` y `templatebody`. Los elementos de plantilla toman la forma de `{key}`, donde `key` es una clave de datos de contexto o una clave de datos convencional. The values available for template expansion are limited to the [standard Lifecycle variables list](/help/ios/metrics.md), in addition to any custom data attached to the hit that triggers the message. En este momento no hay datos basados en el historial o en segmentos disponibles.

También hay plantillas reservadas específicas que el SDK sustituirá automáticamente por usted con datos internos conocidos por el SDK.

Esta lista incluye:

| Nombre del token | Descripción del token |
|--- |--- |
| `{%sdkver%}` | Devuelve la versión del SDK. |
| `{%cachebust%}` | Devuelve un número aleatorio entre 1 y 100 000 000. |
| `{%adid%}` | Devuelve IDFA. Este token solo funciona si se ha utilizado `setAdvertisingIdentifier`. |
| `{%pushid%}` | Devuelve el token de Identificador push. Este token solo funciona si se ha utilizado `setPushIdentifier`. |
| `{%timestampu%}` | Devuelve la marca de fecha y hora actual, en tiempo de época. |
| `{%timestampz%}` | Devuelve la marca de fecha y hora actual en formato JavaScript (ISO 8601). |