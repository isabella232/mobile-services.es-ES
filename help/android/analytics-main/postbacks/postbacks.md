---
description: Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos desencadenadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.
keywords: android, biblioteca, mobile, móvil, sdk
solution: Experience Cloud,Analytics
title: Información general de Postbacks
topic-fix: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
exl-id: 318f6eab-ff71-4bfe-8eb7-51a35380b992
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 100%

---

# Postbacks {#postbacks}

Los postbacks le permiten enviar datos recopilados por el SDK a un servidor de terceros. Con los mismos desencadenadores y las mismas características que se emplean para mostrar un mensaje en la aplicación, es posible configurar el SDK para que envíe datos personalizados a un destino de terceros.

>[!IMPORTANT]
>
>Esta funcionalidad requiere la versión 4.6.0 o posterior del SDK.

Los mensajes postback se ponen en cola y siguen todas las reglas en línea y sin conexión existentes que rigen la recopilación de datos de análisis. Cuando un mensaje coincide (como los mensajes que se visualizan), los mensajes postback no cancelan el resto de los mensajes. Esto permite que se produzcan varios postbacks en la misma visita de análisis. Para ver la definición, consulte la fila *postbacks* en  [Configuración JSON de ADBMobile](/help/android/configuration/json-config/json-config.md).

## Expansiones de plantilla {#section_6758AD05A24C4E9E965F5253294C164A}

Las expansiones de plantilla están disponibles en las propiedades `templateurl` y `templatebody`. Los elementos de plantilla toman la forma `{key}`, donde `key` es una clave de datos de contexto o una clave de datos convencional. Los valores disponibles para expansiones de plantilla se limitan a las [métricas del ciclo vital](/help/android/metrics.md) y a cualquier dato personalizado que esté adjunto a la visita que activa el mensaje. En este momento no hay datos basados en el historial o en segmentos.

También hay plantillas reservadas específicas que el SDK sustituirá de manera automática por datos internos conocidos por el SDK.

Esta lista incluye:

| Nombre del token | Descripción del token |
|--- |--- |
| {%sdkver%} | Devuelve la versión del SDK. |
| {%cachebust%} | Devuelve un número aleatorio entre 1 y 100 000 000. |
| {%adid%} | Devuelve el ID de anunciante para Android. Tenga en cuenta que solo funciona si ha utilizado `submitAdvertisingIdentifierTask`. |
| {%pushid%} | Devuelve el token de Identificador push. Tenga en cuenta que solo funciona si ha utilizado `setPushIdentifier`. |
| {%timestampu%} | Devuelve la marca de fecha y hora actual, en tiempo de época. |
| {%timestampz%} | Devuelve la marca de fecha y hora actual en formato JavaScript (ISO 8601). |
