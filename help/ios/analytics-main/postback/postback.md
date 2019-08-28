---
description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.
seo-description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.
seo-title: Postback
solution: Marketing Cloud, Analytics
title: Información general de Postbacks
uuid: 25 e 2 a 5 fb -1203-40 dd -96 cd-b 23 e 0 f 23376 d
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Información general de Postbacks {#postbacks}

Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.6.0 o posterior del SDK.

Los mensajes postback se ponen en cola y siguen todas las reglas con conexión/sin conexión existentes que controlan la recopilación de datos de análisis. Cuando un mensaje coincide (como los mensajes mostrados), los mensajes postback no cancelan los demás mensajes. Esto permite que aparezcan varios postbacks en la misma visita de análisis. Para ver la definición, consulte la fila *postbacks* en [Configuración JSON de ADBMobile](/help/ios/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in both the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context-data key, or traditional data key. Los valores disponibles para expansiones de plantilla se limitan a la [lista de variables estándar del ciclo vital](/help/ios/metrics.md) y a cualquier dato personalizado que esté adjunto a la visita que activa el mensaje. En la actualidad no están disponibles los datos basados en el historial o en segmentos.

También existen plantillas reservadas específicas que el SDK sustituirá automáticamente por usted con datos internos que el SDK conoce.

Esta lista incluye:

| Nombre del token | Descripción del token |
|--- |--- |
| `{%sdkver%}` | Devuelve la versión del SDK. |
| `{%cachebust%}` | Devuelve un número aleatorio entre 1 y 100 000 000. |
| `{%adid%}` | Devuelve IDFA. Este token solo funciona si se ha utilizado `setAdvertisingIdentifier`. |
| `{%pushid%}` | Devuelve el token de Identificador push. Este token solo funciona si se ha utilizado `setPushIdentifier`. |
| `{%timestampu%}` | Devuelve la marca de fecha y hora actual, en tiempo de época. |
| `{%timestampz%}` | Devuelve la marca de fecha y hora actual en formato JavaScript (ISO 8601). |