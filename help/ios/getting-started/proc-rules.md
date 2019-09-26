---
description: Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes.
seo-description: Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes.
seo-title: Reglas de procesamiento y datos de contexto
solution: Marketing Cloud,Analytics
title: Reglas de procesamiento y datos de contexto
topic: Desarrollador e implementación
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Processing rules and context data{#processing-rules-and-context-data}

Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes.

Para obtener más información, consulte el contenido siguiente:

* [Formación de reglas de procesamiento](https://tv.adobe.com/embed/1181/16506/) en Summit 2013
* Obtener autorización para utilizar reglas de procesamiento

   Para obtener más información sobre las reglas de procesamiento, consulte Introducción a las reglas [de procesamiento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Al trabajar con reglas de procesamiento, recuerde la información siguiente:

* Agrupe las variables de los datos de contexto mediante espacios de nombres, ya que esto le ayuda a mantener un orden lógico.

   Por ejemplo, si quiere recopilar información acerca de un producto, podría definir las siguientes variables:

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

   Esto podría ayudarle *un poco* a la hora de llevar a cabo la asignación que hay que realizar una única vez en las reglas de procesamiento, a costa de perder legibilidad durante la depuración y las futuras actualizaciones de código, que pueden resultarle más difíciles. Como alternativa, use nombres descriptivos para las claves y los valores:

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
>Adobe se reserva el espacio de nombres " `a.`". Aparte de esta restricción, y para evitar conflictos, el único requisito adicional es que las variables de los datos de contexto sean exclusivas en su empresa de inicio de sesión.

