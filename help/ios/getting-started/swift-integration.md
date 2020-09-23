---
description: El SDK para iOS de Adobe Mobile puede integrarse perfectamente en un proyecto de Swift mediante la función Mix and Match de la biblioteca del desarrollador de iOS.
seo-description: El SDK para iOS de Adobe Mobile puede integrarse perfectamente en un proyecto de Swift mediante la función Mix and Match de la biblioteca del desarrollador de iOS.
seo-title: Integración con Swift
solution: Experience Cloud,Analytics
title: Integración con Swift
topic: Developer and implementation
uuid: 5fb77b57-cbf9-4bcf-8b41-65a933bf9336
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 71%

---


# Integración con Swift {#swift-integration}

El SDK para iOS de Adobe Mobile puede integrarse perfectamente en un proyecto de Swift mediante la función Mix and Match de la biblioteca del desarrollador de iOS.

Para obtener más información, consulte [Interoperabilidad de idiomas](https://developer.apple.com/documentation/swift#2984801.html).

Por ejemplo, si utiliza el método de encabezado puente como se describe en la documentación, puede importar el archivo de encabezado del SDK para iOS de Adobe Mobile:

```
#import “ADBMobile.h”
```

Para acceder a los métodos del SDK en sus archivos de Swift, utilice el siguiente formato:

```
ADBMobile.{methodname}
```

