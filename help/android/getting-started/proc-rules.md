---
description: Las reglas de procesamiento se utilizan para copiar los datos que envía en variables de datos de contexto a eVars, props y otras variables con el fin de realizar informes.
solution: Experience Cloud,Analytics
title: Reglas de procesamiento y datos de contexto
topic-fix: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
exl-id: 543201fd-8118-485f-8235-26ec8f9bbb11
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 72%

---

# Reglas de procesamiento y datos de contexto  {#processing-rules-and-context-data}

Las reglas de procesamiento se utilizan para copiar los datos que envía en variables de datos de contexto a eVars, props y otras variables con el fin de realizar informes. Para obtener más información, consulte [Reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Al trabajar con reglas de procesamiento, recuerde la información siguiente:

* Agrupe las variables de datos de contexto mediante Áreas de nombres, ya que esto le ayuda a mantener un orden lógico. Por ejemplo, para recopilar información sobre un producto, puede definir las siguientes variables:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Las variables de datos de contexto se ordenan alfabéticamente en la interfaz de reglas de procesamiento, lo que permite ver rápidamente qué variables están en la misma Área de nombres.

   Evite asignar nombres a las claves de datos de contexto mediante el uso del número de eVar o propiedad:

   ```js
   "eVar1":"jimbo"
   ```

   Esto puede facilitar *ligeramente* la tarea de completar la asignación de una sola vez en las reglas de procesamiento, pero se pierde la legibilidad durante la depuración y las futuras actualizaciones de código, lo que puede resultar más difícil. En su lugar, recomendamos encarecidamente que use nombres descriptivos para claves y valores:

   ```js
   "username":"jimbo"
   ```

* Las variables de contexto que definen eventos de contador deben establecerse en 1:

   ```js
   "logon":"1"
   ```

* Las variables de datos de contexto que definen eventos de aumento pueden tener el evento como clave y la cantidad que se incrementará como valor:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe reserva el espacio de nombres `"a."`. Para evitar choques, el único requisito adicional es que las variables de los datos de contexto sean exclusivas en su empresa de inicio de sesión.
