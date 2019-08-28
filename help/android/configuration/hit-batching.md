---
description: El agrupamiento de visitas permite que las aplicaciones retengan el envío de las visitas hasta que el número de visitas en la cola haya superado el límite configurado.
keywords: android; library; mobile; sdk
seo-description: El agrupamiento de visitas permite que las aplicaciones retengan el envío de las visitas hasta que el número de visitas en la cola haya superado el límite configurado.
seo-title: Agrupamiento de visitas
solution: Marketing Cloud, Analytics
title: Agrupamiento de visitas
topic: Desarrollador e implementación
uuid: ada 35 be 3-242 b -4 b 2 b-a 828-9 bf 998 dd 58 b 5
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Lotes de visitas {#hit-batching}

El agrupamiento de visitas permite que las aplicaciones retengan el envío de las visitas hasta que el número de visitas en la cola haya superado el límite configurado.

>[!IMPORTANT]
>
>Para utilizar el agrupamiento de visitas **,** debe habilitar el seguimiento sin conexión y tener la versión 4.1 o posterior del SDK

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When the value is set to a number greater than 0, the SDK queues the number of hits equal to the *`batchLimit`* value. Una vez que se supera este umbral, se envían todas las visitas en la cola.

Con el agrupamiento de visitas se emplean los siguientes métodos:

* `Analytics.getQueueSize` devuelve un valor `long` con el número de visitas que hay actualmente en la cola de agrupamiento de visitas.

* `Analytics.sendQueuedHits` fuerza a la biblioteca a enviar todas las visitas de la cola, sin importar cuántas haya.
* `Analytics.clearQueue` borra todas las visitas de la cola sin enviarlas.
