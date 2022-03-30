---
description: El SDK para iOS de Adobe Mobile puede integrarse perfectamente en un proyecto de Swift mediante la función Mix and Match de la biblioteca del desarrollador de iOS.
solution: Experience Cloud Services,Analytics
title: Integración con Swift
topic-fix: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
exl-id: 3c1a2e28-53b0-4128-a5d9-d2403885098d
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 100%

---

# Integración con Swift {#swift-integration}

El SDK para iOS de Adobe Mobile puede integrarse perfectamente en un proyecto de Swift mediante la función Mix and Match de la biblioteca del desarrollador de iOS.

Para obtener más información, consulte [Interoperabilidad de idiomas](https://developer.apple.com/documentation/swift#2984801.html).

Por ejemplo, si utiliza el método de encabezado puente como se describe en la documentación, puede importar el archivo de encabezado del SDK para iOS de Adobe Mobile:

```
#import "ADBMobile.h"
```

Para acceder a los métodos del SDK en sus archivos de Swift, utilice el siguiente formato:

```
ADBMobile.{methodname}
```
