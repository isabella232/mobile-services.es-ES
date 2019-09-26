---
description: El agrupamiento de visitas permite a las aplicaciones que tienen habilitado el seguimiento sin conexión retener el envío de visitas hasta que el número de visitas en la cola supera un límite configurable.
seo-description: El agrupamiento de visitas permite a las aplicaciones que tienen habilitado el seguimiento sin conexión retener el envío de visitas hasta que el número de visitas en la cola supera un límite configurable.
seo-title: Agrupamiento de visitas
solution: Marketing Cloud,Analytics
title: Agrupamiento de visitas
topic: Desarrollador e implementación
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Lotes de visitas {#hit-batching}

El agrupamiento de visitas permite a las aplicaciones que tienen habilitado el seguimiento sin conexión retener el envío de visitas hasta que el número de visitas en la cola supera un límite configurable.

>[!IMPORTANT]
>
>Hit batching requires SDK version 4.1 or later.

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Cuando establece un número mayor que 0, el SDK va poniendo en cola un número de visitas igual a *`batchLimit`*. Una vez que se supera este umbral, se envían todas las visitas en la cola.

Con el agrupamiento de visitas se emplean los siguientes métodos:

* `trackingGetQueueSize()` devuelve un valor `NSUInteger` con el número de visitas que hay actualmente en la cola de agrupamiento de visitas.
* `trackingSendQueuedHits()` fuerza a la biblioteca a que envíe todas las visitas en la cola, sin importar cuántas haya.
* `trackingClearQueue()` borra todas las visitas de la cola sin enviarlas.

>[!CAUTION]
>
>El seguimiento sin conexión debe estar habilitado para utilizar el agrupamiento de visitas.

