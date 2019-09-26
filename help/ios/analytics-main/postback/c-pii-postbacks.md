---
description: Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII, por sus siglas en inglés) y enviarla a un punto final de terceros.
seo-description: Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII, por sus siglas en inglés) y enviarla a un punto final de terceros.
seo-title: Postbacks PII
title: Postbacks PII
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# PII postbacks {#pii-postbacks}

Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII, por sus siglas en inglés) y enviarla a un punto final de terceros.

Cuando quiera utilizar el SDK de Adobe para recopilar PII, debe enviar una llamada de seguimiento PII. Aunque el uso de esta llamada habilita la recopilación de datos PII, el SDK no envía automáticamente los datos a ningún punto final de Adobe. Se debe configurar un postback de tipo PII con el punto final apropiado.

>[!TIP]
>
>Se requiere un punto final que admita HTTPS para utilizar el tipo de postback PII.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración al proyecto* en Implementación [principal y ciclo de vida](/help/ios/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Cuando esté preparado para capturar PII, llame a `trackPII` para enviar una visita para esta acción, evento o vista:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```

