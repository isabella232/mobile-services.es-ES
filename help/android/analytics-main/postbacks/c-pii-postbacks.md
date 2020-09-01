---
description: Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII) y enviarla a un punto final de terceros.
seo-description: Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII) y enviarla a un punto final de terceros.
seo-title: Postbacks PII
title: Postbacks PII
uuid: 8d1f1fb8-6842-478b-a164-e7f727755bd9
translation-type: ht
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: ht
source-wordcount: '182'
ht-degree: 100%

---


# Postbacks PII {#pii-postbacks}

Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII) y enviarla a un punto final de terceros.

Si desea utilizar el SDK de Adobe para recopilar PII, debe enviar una llamada de seguimiento PII. Aunque el uso de esta llamada habilita la recopilación de PII, el SDK no envía automáticamente los datos a un punto final de Adobe. Se debe configurar un postback de tipo PII con el punto final apropiado.

>[!TIP]
>
>Se requiere un punto final compatible con HTTPS para utilizar el tipo PII de postback.

## Seguimiento de postbacks PII {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).

1. Importe la biblioteca:

   ```java
   #import "ADBMobile.h"
   ```

1. Cuando esté preparado para capturar PII, llame a `trackPII` para enviar una visita para esta acción, evento o vista:

   ```java
   Config.collectPII(new HashMap<String, Object>(){{
     put("key","value");
   }});
   ```

