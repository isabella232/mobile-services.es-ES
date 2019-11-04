---
description: Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la duración de cada sesión y el tiempo total entre sesiones que la acción tarda en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.
seo-description: Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la duración de cada sesión y el tiempo total entre sesiones que la acción tarda en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.
seo-title: Acciones temporizadas
solution: Experience Cloud,Analytics
title: Acciones temporizadas
topic: Desarrollador e implementación
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
translation-type: ht
source-git-commit: 97c0dc17bcc624b38e9eb8023eb1d69d02568d11

---


# Acciones temporizadas {#timed-actions}

Las acciones temporizadas le permiten medir el tiempo en la aplicación y el tiempo total entre el comienzo y el final de una acción. El SDK calcula la duración de cada sesión y el tiempo total entre sesiones que la acción tarda en completarse. Puede utilizar acciones temporizadas para definir segmentos y comparar tiempos de compra, niveles de pase, flujos de cierre de compra, etcétera.

Para las acciones temporizadas se comunican las siguientes métricas:

* Total de segundos en la aplicación entre inicio y final (entre sesiones)
* Total de segundos entre inicio y final (tiempo de reloj)

Una llamada de retorno opcional le permite realizar acciones adicionales cuando se completa la acción temporizada:

* Ejecutar código y agregar cualquier lógica: lógica personalizada opcional basada en los resultados de duración.
* Agregar datos de contexto antes de pasar las duraciones.
* Cancelar visitas y duraciones no enviadas todavía.

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

