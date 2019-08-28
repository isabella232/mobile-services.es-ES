---
description: Esta información le ayuda a comprender cómo se realiza el seguimiento de bloqueos y cuáles son las prácticas recomendadas para encargarse de los falsos bloqueos.
seo-description: Esta información le ayuda a comprender cómo se realiza el seguimiento de bloqueos y cuáles son las prácticas recomendadas para encargarse de los falsos bloqueos.
seo-title: Seguimiento de errores de aplicación
solution: Marketing Cloud, Analytics
title: Seguimiento de bloqueos de aplicaciones
topic: Desarrollador e implementación
uuid: 4 f 81988 b -198 a -4 ba 9-ad 53-78 af 90 e 43856
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Seguimiento de errores de aplicaciones {#track-app-crashes}

Esta información le ayuda a comprender cómo se realiza el seguimiento de bloqueos y cuáles son las prácticas recomendadas para encargarse de los falsos bloqueos.

>[!IMPORTANT]
>
>Debe actualizar a la versión 4.8.6 de iOS SDK, que contiene cambios críticos que impiden que se puedan crear informes falsos bloqueos.

## ¿Cuándo comunica Adobe un bloqueo?

Si la aplicación termina sin haber sido antes puesta en segundo plano, el SDK comunica un bloqueo la próxima vez que la inicie.

## ¿Cómo funciona la comunicación de bloqueos?

iOS utiliza notificaciones del sistema que permiten a los desarrolladores realizar un seguimiento y responder a distintos estados y eventos en el ciclo vital de la aplicación.

El SDK para iOS de Adobe Mobile tiene un controlador de notificación que responde a la notificación `UIApplicationDidEnterBackgroundNotification`. En este código se establece un valor que indica que el usuario ha puesto la aplicación en segundo plano. Si en el siguiente inicio no se encuentra dicho valor, se informa de un bloqueo.

## ¿Por qué mide Adobe los bloqueos de este modo?

Este enfoque de la medición de bloqueos proporciona una respuesta de alto nivel a la pregunta: *¿salió el usuario de mi aplicación de forma intencionada?*

Las bibliotecas de informes de bloqueos que proporcionan empresas como Apteligent (antes Crittercism) utilizan un controlador `NSException` global para ofrecer informes de bloqueo más detallados. Una aplicación no puede tener más de uno de estos controladores. Adobe ha decidido no implementar un controlador `NSException` global para evitar errores de compilación, sabiendo que los clientes podrían estar utilizando otros proveedores de informes de bloqueo.

## ¿Qué puede provocar que se comunique un falso bloqueo?

Se sabe que las siguientes situaciones pueden provocar que el SDK comunique equivocadamente un bloqueo:

* Si está depurando con Xcode, volver a iniciar la aplicación mientras está en primer plano provoca un bloqueo.

   >[!TIP]
   >
   >Puede evitar un bloqueo en este escenario poniendo en segundo plano la aplicación antes de volver a iniciarla desde Xcode.

* If your app is in the background and sends Analytics hits through a call other than `trackActionFromBackground`, `trackLocation`, or `trackBeacon`, and the app is terminated (manually or by the OS) while in the background, and the next launch will be a crash.

   >[!TIP]
   >
   >Background activity that occurs beyond the `lifecycleTimeout` threshold might also result in an additional false launch.

* Si la aplicación se inicia en segundo plano (como resultado de una captura en segundo plano, una actualización de ubicación, etcétera) y el sistema operativo la cierra sin pasar al primer plano, el siguiente inicio (ya sea en primer o en segundo plano) resulta en un bloqueo.
* Si elimina mediante programación la marca de pausa de Adobe de `NSUserDefaults` mientras la aplicación está en segundo plano, el siguiente inicio o reanudación provoca un bloqueo.

## ¿Cómo puedo impedir que se comuniquen falsos bloqueos?

Las siguientes recomendaciones pueden ayudar a prevenir la comunicación de falsos bloqueos:

* En el SDK para iOS 4.8.6, se agregó un código que determina con más precisión si una nueva sesión de ciclo vital es deseada o no.

   Este código resuelve los falsos bloqueos 2 y 3 indicados en la sección anterior.

* Asegúrese de realizar el desarrollo con grupos de informes de no producción. Esto debería evitar que se produzca el caso 1 de falso bloqueo.
* No elimine o modifique ningún valor que el SDK de Adobe Mobile ponga en `NSUserDefaults`.

   Si estos valores se modifican fuera del SDK, los datos informados no serán válidos.

