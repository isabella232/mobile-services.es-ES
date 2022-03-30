---
description: El agrupamiento de visitas permite que las aplicaciones retengan el envío de las visitas hasta que el número de visitas en la cola haya superado el límite configurado.
keywords: android, biblioteca, mobile, móvil, sdk
solution: Experience Cloud Services,Analytics
title: Agrupamiento de visitas
topic-fix: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
exl-id: 74147f09-52fc-46dc-b4dd-2bf60b039f6e
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 100%

---

# Agrupamiento de visitas {#hit-batching}

El agrupamiento de visitas permite que las aplicaciones retengan el envío de las visitas hasta que el número de visitas en la cola haya superado el límite configurado.

>[!IMPORTANT]
>
>Para utilizar el agrupamiento de visitas, **debe** habilitar el seguimiento sin conexión y tener la versión 4.1 o posterior del SDK

Para habilitar el agrupamiento de visitas, actualice el archivo `ADBMobileConfig.json` y especifique un valor para `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Si el valor se establece en un número mayor que 0, el SDK pondrá en cola un número de visitas igual al valor *`batchLimit`*. Después de superar este umbral, se envían todas las visitas en la cola.

Con el agrupamiento de visitas, se utilizan los siguientes métodos:

* `Analytics.getQueueSize` devuelve un valor `long` con el número de visitas que hay actualmente en la cola de agrupamiento de visitas.

* `Analytics.sendQueuedHits` fuerza a la biblioteca a enviar todas las visitas de la cola, sin importar cuántas haya.
* `Analytics.clearQueue` borra todas las visitas de la cola sin enviarlas.
