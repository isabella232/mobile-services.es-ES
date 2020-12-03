---
description: Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes.
seo-description: Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes.
seo-title: Reglas de procesamiento y datos de contexto
solution: Experience Cloud,Analytics
title: Reglas de procesamiento y datos de contexto
topic: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 100%

---


# Reglas de procesamiento y datos de contexto {#processing-rules-and-context-data}

Se utilizan reglas de procesamiento para copiar los datos que envía en variables de datos de contexto a evars, props y otras variables con el fin de realizar informes.

Para obtener más información, consulte el contenido siguiente:

* [Formación sobre reglas de procesamiento](https://tv.adobe.com/embed/1181/16506/) en Summit 2013
* Obtenga autorización para utilizar reglas de procesamiento

   Para obtener más información sobre las reglas de procesamiento, consulte [Información general sobre las reglas de procesamiento](https://docs.adobe.com/content/help/es-ES/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Al trabajar con reglas de procesamiento, recuerde la información siguiente:

* Agrupe las variables de datos de contexto mediante Áreas de nombres, ya que esto le ayuda a mantener un orden lógico.

   Por ejemplo, si desea recopilar información sobre un producto, puede definir las siguientes variables:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Las variables de datos de contexto se ordenan alfabéticamente en la interfaz de reglas de procesamiento, lo que permite ver rápidamente qué variables están en la misma Área de nombres.

   Evite asignar nombres a las claves de datos de contexto mediante el uso del número de eVar o prop:

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

