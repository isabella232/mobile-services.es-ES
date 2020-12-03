---
description: El agrupamiento de visitas permite a las aplicaciones que tienen habilitado el seguimiento sin conexión retener el envío de visitas hasta que el número de visitas en la cola supera un límite configurable.
seo-description: El agrupamiento de visitas permite a las aplicaciones que tienen habilitado el seguimiento sin conexión retener el envío de visitas hasta que el número de visitas en la cola supera un límite configurable.
seo-title: Agrupamiento de visitas
solution: Experience Cloud,Analytics
title: Agrupamiento de visitas
topic: Developer and implementation
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 100%

---


# Lotes de visitas {#hit-batching}

El agrupamiento de visitas permite a las aplicaciones que tienen habilitado el seguimiento sin conexión retener el envío de visitas hasta que el número de visitas en la cola supera un límite configurable.

>[!IMPORTANT]
>
>El agrupamiento de visitas requiere la versión 4.1 o posterior del SDK.

Para habilitar el agrupamiento de visitas, actualice el archivo `ADBMobileConfig.json` y especifique un valor para `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Cuando establece un número mayor que 0, el SDK va poniendo en cola un número de visitas igual a *`batchLimit`*. Después de superar este umbral, se envían todas las visitas en la cola.

Con el agrupamiento de visitas, se utilizan los siguientes métodos:

* `trackingGetQueueSize()` devuelve un valor `NSUInteger` con el número de visitas que hay actualmente en la cola de agrupamiento de visitas.
* `trackingSendQueuedHits()` fuerza a la biblioteca a que envíe todas las visitas en la cola, sin importar cuántas haya.
* `trackingClearQueue()` borra todas las visitas de la cola sin enviarlas.

>[!CAUTION]
>
>El seguimiento sin conexión debe estar habilitado para utilizar el agrupamiento de visitas.

