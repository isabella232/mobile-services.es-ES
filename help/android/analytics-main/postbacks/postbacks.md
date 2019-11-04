---
description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Información general de Postbacks
topic: Desarrollador e implementación
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: ht
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postbacks {#postbacks}

Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos activadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.6.0 o posterior del SDK.

Los mensajes postback se ponen en cola y siguen todas las reglas con conexión/sin conexión existentes que controlan la recopilación de datos de análisis. Cuando un mensaje coincide (como los mensajes mostrados), los mensajes postback no cancelan los demás mensajes. Esto permite que aparezcan varios postbacks en la misma visita de análisis. Para ver la definición, consulte la fila *postbacks* en [Configuración JSON de ADBMobile](/help/android/configuration/json-config/json-config.md).

## Expansiones de plantilla {#section_6758AD05A24C4E9E965F5253294C164A}

Las expansiones de plantilla están disponibles en las propiedades `templateurl` y `templatebody`. Los elementos de plantilla toman la forma `{key}`, donde `key` es una clave de datos de contexto o una clave de datos convencional. Los valores disponibles para expansiones de plantilla se limitan a las [métricas del ciclo vital](/help/android/metrics.md) y a cualquier dato personalizado que esté adjunto a la visita que activa el mensaje. En la actualidad no están disponibles los datos basados en el historial o en segmentos.

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