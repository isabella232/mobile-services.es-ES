---
description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.
keywords: android;library;mobile;sdk
seo-description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.
seo-title: Postback
solution: Marketing Cloud,Analytics
title: Postbacks overview
topic: Desarrollador e implementación
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postbacks {#postbacks}

Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.6.0 o posterior del SDK.

Los mensajes postback se ponen en cola y siguen todas las reglas con conexión/sin conexión existentes que controlan la recopilación de datos de análisis. Cuando un mensaje coincide (como los mensajes mostrados), los mensajes postback no cancelan los demás mensajes. Esto permite que aparezcan varios postbacks en la misma visita de análisis. Para ver la definición, consulte la fila *postbacks* en [Configuración JSON de ADBMobile](/help/android/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context data key or traditional data key. The values that are available for template expansion are limited to the [Lifecycle metrics](/help/android/metrics.md), in addition to any custom data that is attached to the hit that triggers the message. En la actualidad no están disponibles los datos basados en el historial o en segmentos.

También existen plantillas reservadas específicas que el SDK sustituirá automáticamente con datos internos que el SDK conoce.

Esta lista incluye:

| Nombre del token | Descripción del token |
|--- |--- |
| {%sdkver%} | Devuelve la versión del SDK. |
| {%cachebust%} | Devuelve un número aleatorio entre 1 y 100 000 000. |
| {%adid%} | Devuelve el ID de anunciante para Android. Tenga en cuenta que solo funciona si ha utilizado `submitAdvertisingIdentifierTask`. |
| {%pushid%} | Devuelve el token de Identificador push. Tenga en cuenta que solo funciona si ha utilizado `setPushIdentifier`. |
| {%timestampu%} | Devuelve la marca de fecha y hora actual, en tiempo de época. |
| {%timestampz%} | Devuelve la marca de fecha y hora actual en formato JavaScript (ISO 8601). |