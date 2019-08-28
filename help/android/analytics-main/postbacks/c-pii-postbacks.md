---
description: Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII, por sus siglas en inglés) y enviarla a un punto final de terceros.
seo-description: Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII, por sus siglas en inglés) y enviarla a un punto final de terceros.
seo-title: Postbacks PII
title: Postbacks PII
uuid: 8 d 1 f 1 fb 8-6842-478 b-a 164-e 7 f 727755 bd 9
translation-type: tm+mt
source-git-commit: 70ac08c74e11a68d94d3f10ed6d7fc133d34149d

---


# PII postbacks {#pii-postbacks}

Puede utilizar el SDK de Adobe para recopilar información de identificación personal (PII, por sus siglas en inglés) y enviarla a un punto final de terceros.

Cuando quiera utilizar el SDK de Adobe para recopilar PII, debe enviar una llamada de seguimiento PII. Aunque el uso de esta llamada habilita la recopilación de datos PII, el SDK no envía automáticamente los datos a un punto de conexión de Adobe. Se debe configurar un postback de tipo PII con el punto final apropiado.

>[!TIP]
>
>Se requiere un punto final compatible con HTTPS para utilizar el tipo de postback PII.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Agregue [la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto intellij IDEA o Eclipse* en [implementación y ciclo vital de Core](/help/android/getting-started/dev-qs.md).

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

