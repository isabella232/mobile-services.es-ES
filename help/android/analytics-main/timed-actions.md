---
description: Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo de cada sesión y el tiempo total entre sesiones que tardará la acción en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.
solution: Experience Cloud Services,Analytics
title: Acciones temporizadas
topic-fix: Developer and implementation
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
exl-id: d9851440-6e65-4d89-a6b3-81c8abd2bf06
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 100%

---

# Acciones temporizadas {#timed-actions}

Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la cantidad de tiempo de cada sesión y el tiempo total entre sesiones que tardará la acción en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.

Las siguientes métricas se incluyen en los informes para acciones temporizadas:

* Total de segundos en la aplicación entre inicio y finalización (entre sesiones)
* Total de segundos entre el inicio y el final (hora del reloj)

Una llamada de retorno opcional le permite realizar acciones adicionales cuando finaliza la acción temporizada:

* Ejecute el código y agregue cualquier lógica: lógica personalizada opcional basada en los resultados de duración.
* Añada datos de contexto antes de pasar duraciones.
* Cancele visitas y duraciones aún no enviadas.

## Seguimiento de acciones temporizadas {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Agregue la biblioteca al proyecto e implemente el ciclo vital.

   Para obtener más información, consulte *Agregar el SDK y el archivo de configuración a su proyecto IntelliJ IDEA o Eclipse* en [Implementación principal y ciclo de vida](/help/android/getting-started/dev-qs.md).
1. Importe la biblioteca:

   ```java
   import com.adobe.mobile.*;
   ```

1. Llame a `trackTimedActionStart` y proporcione un nombre de acción temporizada y datos de contexto opcionales.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. (Opcional) En cualquier momento puede llamar a `trackTimedActionUpdate` con el nombre de la acción temporizada para agregar datos de contexto adicionales.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. Cuando el evento se complete, llame a `trackTimedActionEnd` y transfiera el nombre de la acción temporizada y `TimedActionBlock` (llamada de retorno), que buscará todos los datos y calculará las duraciones.

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   Las métricas de eventos temporizados se guardan en variables de soluciones móviles para la realización automática de informes.

## Envío de datos adicionales {#section_3EBE813E54A24F6FB669B2478B5661F9}

Además del nombre de la acción temporizada, también puede enviar datos de contexto adicionales con las llamadas de inicio y actualización de acción:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
```

El valor de los datos de contexto debe asignarse a variables personalizadas de Adobe Mobile Services:

![](assets/map-variable-context-ltv.png)

## Ejemplos {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```java
// Timed Action Start Example 
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("ExperienceName", experience); 
Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
 
// Timed Action Update Example 
cdata = new HashMap<String, Object>(); 
cdata.put("ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata); 
 
// Timed Action End Example 
Analytics.trackTimedActionEnd("TimeUntilPurchase", null); 
 
// Timed Action End Example with Callback 
Analytics.trackTimedActionEnd("TimeUntilPurchase", new Analytics.TimedActionBlock<Boolean>() { 
 @Override 
 public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) { 
  contextData.put("PurchaseItem", "Item453"); 
  return true; // return true to send the hit, false to cancel 
 } 
});
```
