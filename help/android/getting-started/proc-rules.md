---
description: Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes.
seo-description: Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes.
seo-title: Reglas de procesamiento y datos de contexto
solution: Marketing Cloud,Analytics
title: Reglas de procesamiento y datos de contexto
topic: Desarrollador e implementación
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Processing rules and context data {#processing-rules-and-context-data}

Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes. For more information, see [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Al trabajar con reglas de procesamiento, recuerde la información siguiente:

* Agrupe las variables de los datos de contexto mediante espacios de nombres, ya que esto le ayuda a mantener un orden lógico. Por ejemplo, para recopilar información acerca de un producto, podría definir las siguientes variables:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Las variables de datos de contexto se ordenan alfabéticamente en la interfaz de reglas de procesamiento, lo que le permite ver rápidamente qué variables hay en el mismo espacio de nombres.

   Evite dar nombre a las claves de datos de contexto utilizando el número de eVar o propiedad:

   ```js
   "eVar1":"jimbo"
   ```

   Esto podría ayudarle *un poco* a la hora de completar la asignación que hay que realizar una única vez en las reglas de procesamiento, a costa de perder legibilidad durante la depuración y las futuras actualizaciones de código, que pueden resultarle más difíciles. Lo que se recomienda encarecidamente es utilizar nombres descriptivos para las claves y valores:

   ```js
   "username":"jimbo"
   ```

* Las variables de contexto que definen eventos de contador deberían establecerse en 1:

   ```js
   "logon":"1"
   ```

* Las variables de contexto que definen eventos de aumento pueden tener el evento como clave y la cantidad a incrementar como valor:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe reserves the namespace . `"a."` Para evitar choques, el único requisito adicional es que las variables de los datos de contexto sean exclusivas en su empresa de inicio de sesión.

