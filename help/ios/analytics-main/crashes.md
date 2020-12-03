---
description: Esta información le ayuda a comprender cómo se realiza el seguimiento de bloqueos y cuáles son las prácticas recomendadas para encargarse de los falsos bloqueos.
seo-description: Esta información le ayuda a comprender cómo se realiza el seguimiento de bloqueos y cuáles son las prácticas recomendadas para encargarse de los falsos bloqueos.
seo-title: Seguimiento de bloqueos de aplicaciones
solution: Experience Cloud,Analytics
title: Seguimiento de bloqueos de aplicaciones
topic: Developer and implementation
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 100%

---


# Seguimiento de errores de aplicaciones {#track-app-crashes}

Esta información le ayuda a comprender cómo se realiza el seguimiento de bloqueos y cuáles son las prácticas recomendadas para encargarse de los falsos bloqueos.

>[!IMPORTANT]
>
>Debería actualizar a la versión 4.8.6 del SDK para iOS, que contiene cambios esenciales que impiden que se comuniquen falsos bloqueos.

## ¿Cuándo comunica Adobe un bloqueo?

Si la aplicación termina sin haber sido antes puesta en segundo plano, el SDK comunica un bloqueo la próxima vez que la inicie.

## ¿Cómo funciona la comunicación de bloqueos?

iOS utiliza notificaciones del sistema que permiten a los desarrolladores realizar un seguimiento y responder a distintos estados y eventos en el ciclo vital de la aplicación.

El SDK para iOS de Adobe Mobile tiene un controlador de notificación que responde a la notificación `UIApplicationDidEnterBackgroundNotification`. En este código, se establece un valor que indica que el usuario ha puesto la aplicación en segundo plano. En un lanzamiento posterior, si no se encuentra ese valor, se informa un bloqueo.

## ¿Por qué mide Adobe los bloqueos de este modo?

Este enfoque de la medición de bloqueos proporciona una respuesta de alto nivel a la pregunta: *¿salió el usuario de mi aplicación de forma intencionada?*

Las bibliotecas de informes de bloqueos que proporcionan empresas como Apteligent (antes Crittercism) utilizan un controlador `NSException` global para ofrecer informes de bloqueo más detallados. Una aplicación no puede tener más de uno de estos controladores. Adobe ha decidido no implementar un controlador `NSException` global para evitar errores de compilación, sabiendo que los clientes podrían estar utilizando otros proveedores de informes de bloqueo.

## ¿Qué puede provocar que se comunique un falso bloqueo?

Se sabe que los siguientes escenarios causan incorrectamente que el SDK informe un bloqueo:

* Si está depurando con Xcode, volver a iniciar la aplicación mientras está en primer plano provoca un bloqueo.

   >[!TIP]
   >
   >En esta situación, puede evitar el bloqueo poniendo la aplicación en segundo plano antes de volver a iniciarla desde Xcode.

* Si la aplicación está en segundo plano y envía visitas de Analytics mediante una llamada distinta de `trackActionFromBackground`, `trackLocation`, o `trackBeacon`, y después se cierra (de forma manual o por el sistema operativo) mientras está en segundo plano, al volver a iniciarse se producirá un bloqueo.

   >[!TIP]
   >
   >La actividad en segundo plano que se produce más allá del umbral de `lifecycleTimeout` también podría resultar en un falso inicio.

* Si la aplicación se inicia en segundo plano (como resultado de una captura en segundo plano, una actualización de ubicación, etcétera) y el sistema operativo la cierra sin pasar al primer plano, el siguiente inicio (ya sea en primer o en segundo plano) resulta en un bloqueo.
* Si elimina mediante programación la marca de pausa de Adobe de `NSUserDefaults` mientras la aplicación está en segundo plano, el siguiente inicio o reanudación provoca un bloqueo.

## ¿Cómo puedo impedir que se comuniquen falsos bloqueos?

Las siguientes recomendaciones pueden ayudar a prevenir la comunicación de falsos bloqueos:

* En el SDK para iOS 4.8.6, se agregó código para determinar mejor si se desea una nueva sesión de ciclo vital.

   Este código corrige los falsos bloqueos 2 y 3 en la sección anterior.

* Asegúrese de realizar el desarrollo con los grupos de informes que no sean de producción, lo que debería evitar que se produzca el falso bloqueo 1.
* No elimine o modifique ningún valor que el SDK de Adobe Mobile ponga en `NSUserDefaults`.

   Si se modifican estos valores desde fuera del SDK, los datos comunicados no serán válidos.

