---
description: Al personalizar informes, la gran flexibilidad puede suscitar algunas preguntas referentes a cuál es el mejor tipo de informe para obtener los datos que necesita.
keywords: mobile
seo-description: Al personalizar informes, la gran flexibilidad puede suscitar algunas preguntas referentes a cuál es el mejor tipo de informe para obtener los datos que necesita.
seo-title: Tipos de informes
solution: Marketing Cloud, Analytics
title: Tipos de informes
topic: Informes, métricas
uuid: 8747 b 11 e -31 b 1-47 bc-ad 55-db 5 ab 4 ef 7078
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Tipos de informes {#report-types}

Al personalizar informes, la gran flexibilidad puede suscitar algunas preguntas referentes a cuál es el mejor tipo de informe para obtener los datos que necesita.

Antes de personalizar los informes, debe conocer la diferencia entre una métrica y una dimensión.

* Métrica

   Una métrica se usa para medir sus datos. Las métricas son valores que se pueden contar y sumar, y se usan para ver con qué frecuencia ocurren acciones específicas en su aplicación. Entre las métricas comunes se incluyen: instalaciones, lanzamientos, ingresos, valores de duración e inicios de sesión. Por ejemplo, cada vez que se inicia su aplicación, el valor de los _ launches_ value se incrementa en uno.

* Dimensión

   Una dimensión se usa para describir sus datos. Las dimensiones se representan usando una cadena o un número que actúa como una cadena (como un código postal, y se utiliza para organizar y segmentar los datos. La versión del sistema operativo, el nombre de la campaña, el nombre del producto y el operador de telefonía móvil son ejemplos de dimensiones comunes. Cada dimensión tiene un número de valores concretos que están asociados a ella. For example, the OS version dimension has values such as _iOS 7_ and _Android 4.1.2_.

Estos son los tipos de informes que se pueden generar en la interfaz de usuario de Mobile:

## Informe de horas extras {#section_2741DA54C90C49AFB17C7B9BC7AD627D}

Los informes de horas extras muestran la evolución de las métricas a lo largo de un intervalo de tiempo para que pueda identificar rápidamente picos y tendencias. El análisis se inicia a menudo en un informe de horas extras y, después, se traslada a un informe de clasificación y tendencias al realizar el desglose para investigar los factores que pueden estar contribuyendo a una tendencia o un pico de métrica.

Por ejemplo, si ve un pico en los inicios, puede ejecutar un informe de tendencias que muestre los inicios de los 5 sistemas operativos más importantes para ver cuál de ellos contribuye más a este pico:

![](assets/overtime.png)

Para ver valores de dimensión con otras métricas en un informe de horas extras, puede usar la métrica de instancias y definir un filtro de dimensión.

## Informe de tendencias {#section_C9BE9A2EDBFF4D938B9AF14C8AA67883}

Los informes de tendencias sirven para ver la evolución de sus dimensiones más populares en relación con una métrica. Puede usar este informe para determinar cuáles son los valores que más contribuyen a un cambio en una métrica.

![](assets/trended.png)

Para ver el informe de tendencias de una dimensión, agregue un filtro adhesivo (por ejemplo, sistema operativo = iOS 6.0.1) a un informe de horas extras para ver los mismos datos. Además, puede agregar cinco métricas adicionales al informe filtrado de horas extras.

## Informe de horas extras filtrado {#section_F8FAF2A4496F449CA99EF1E052C71A2D}

Si desea ver un valor de dimensión específico, puede agregar un filtro adhesivo a un informe de horas extras. En el informe siguiente se muestran 30 días de inicios, actualizaciones y errores de una versión de sistema operativo concreta.

![](assets/overtime-filter.png)

## Informe de clasificación {#section_C073D744A95843AF99EE74FB5B013735}

Los informes de clasificación muestran con qué frecuencia las 50 dimensiones más importantes contribuyen a una métrica. Este informe es útil para ver la contribución total de un intervalo de fechas en un conjunto de muchos valores.

![](assets/ranked.png)

## Informe radial {#section_17A9842039174DE094A6B1E9837E35BB}

Los informes radiales proporcionan, por ejemplo, el informe base junto con desgloses. La visualización utiliza la altura para mostrar la métrica y las diferencias de rendimiento entre las métricas. Cada círculo concéntrico representa un segmento de audiencia en la categoría de ese círculo. Puede realizar acciones en una audiencia, como aplicar un filtro adhesivo y ocultar o ver métricas.

Puede ver el informe y un tutorial en el producto que describe cómo interactuar con un gráfico de destello solar.

Para iniciar el tutorial:

1. En Administrar configuración de aplicación, haga clic en **[!UICONTROL Uso]**.

1. Click **[!UICONTROL Technology]** &gt; **[!UICONTROL Technology Breakdown]**.
1. In the title bar of the report, click **[!UICONTROL Customize]**, and click the information icon.

![](assets/report_technology.png)

### Informe de rutas {#section_AD400106BC684B50B27CCCD3F4497114}

Un informe de rutas se basa en el análisis de estas y muestra un gráfico que representa las rutas que han pasado de un estado a otro en la aplicación.

![](assets/action_paths.png)

Los nodos tienen forma de caja y representan un estado en las rutas de los usuarios a través de una aplicación. Por ejemplo, en la ilustración anterior, el nodo principal representa el número de usuarios que han iniciado la aplicación y han seleccionado una fotografía de la galería.

### Informe Embudo {#section_AF3B0C899D844FC3AD1F91A2C452C92F}

El informe Embudo sirve para identificar el punto en el que los clientes abandonan una campaña de marketing o se desvían de una ruta de conversión definida al interactuar con la aplicación móvil. Asimismo, puede utilizar el informe Embudo para comparar las acciones de diferentes segmentos.

La visualización del canal le permite ver el punto en el que los clientes salen del proceso. El aumento de la visibilidad de las decisiones de los clientes en cada paso permite ver en qué momento pierden el interés, la ruta que suelen seguir y el momento en el que abandonan la aplicación.

![](assets/funnel.png)
