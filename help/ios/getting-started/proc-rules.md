---
description: Las reglas de procesamiento se utilizan para copiar los datos que envía en variables de datos de contexto a eVars, props y otras variables con el fin de realizar informes.
solution: Experience Cloud,Analytics
title: Reglas de procesamiento y datos de contexto
topic-fix: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
exl-id: a3968160-42c4-4671-b541-c14639b8a451
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 70%

---

# Reglas de procesamiento y datos de contexto {#processing-rules-and-context-data}

Las reglas de procesamiento se utilizan para copiar los datos que envía en variables de datos de contexto a eVars, props y otras variables con el fin de realizar informes.

Para obtener más información, consulte el contenido siguiente:

* [Formación sobre reglas de procesamiento](https://tv.adobe.com/embed/1181/16506/) en Summit 2013
* Obtenga autorización para utilizar reglas de procesamiento

   Para obtener más información sobre las reglas de procesamiento, consulte [Información general sobre las reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) en la documentación de Adobe Analytics.

Al trabajar con reglas de procesamiento, recuerde la información siguiente:

* Agrupe las variables de datos de contexto mediante Áreas de nombres, ya que esto le ayuda a mantener un orden lógico.

   Por ejemplo, si desea recopilar información sobre un producto, puede definir las siguientes variables:

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

   Esto puede facilitar *ligeramente* la tarea de asignar de una sola vez en las reglas de procesamiento, pero se pierde la legibilidad durante la depuración y las futuras actualizaciones de código, lo que puede resultar más difícil. En su lugar, utilice nombres descriptivos para las claves y los valores:

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
>Adobe reserva el espacio de nombres &quot;`a.`&quot;. Aparte de esta restricción, y para evitar conflictos, el único requisito adicional es que las variables de los datos de contexto sean exclusivas en su empresa de inicio de sesión.
