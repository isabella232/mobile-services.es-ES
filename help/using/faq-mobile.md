---
description: Preguntas más frecuentes y respuestas sobre Adobe Mobile Services, además de una descripción general de las funciones.
keywords: móvil
solution: Experience Cloud Services,Analytics
title: Preguntas frecuentes
topic-fix: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
exl-id: d7dfc36e-56f0-498a-ad50-93fee90cb6ff
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 96%

---

# Preguntas frecuentes {#frequently-asked-questions}

{#eol}

La siguiente tabla contiene una lista de preguntas frecuentes sobre Adobe Mobile Services:

## SDK de Adobe Mobile {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### ¿Qué versión del SDK debería tener?

Nuestros SDK actuales están en la versión 4.11. Para obtener más información, consulte la [Notas de versión](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=es).

### ¿Dónde puedo descargar los SDK?

Los SDK para plataformas móviles individuales se pueden descargar desde la sección [Administrar configuración de la aplicación](/help/using/c-manage-app-settings/c-manage-app-settings.md).

### ¿Cómo configuro los SDK?

Tras crear un nuevo grupo de informes para la aplicación, vaya a Administrar configuración de la aplicación y configure todas las opciones necesarias en la página de información de la aplicación. Una vez guardada la configuración, descargue los SDK necesarios desde la parte inferior de la página Administrar configuración de aplicación. El SDK se habrá preconfigurado con las opciones que ha guardado; se puede encontrar en el archivo `ADBMobileConfig.json` del paquete de SDK. Si cambia cualquier configuración del SDK en la página Administrar configuración de la aplicación, vuelva a descargar los archivos SDK o actualice el archivo `ADBMobileConfig.json` con los cambios necesarios.

### ¿Los SDK de Adobe Mobile son compatibles con IPv6 para iOS?

Los SDK de Adobe Mobile utilizan las pilas de red estándar de iOS y Android. Para iOS, el SDK utiliza NSURLSession (iOS versión 7 y posteriores) y NSURLConnection (iOS versión 7 y posteriores), totalmente compatibles con IPv6. Puede que los desarrolladores que hayan creado o que utilicen su propia pila de red deseen comprobar si hay otras consideraciones que faciliten el proceso. A continuación se muestra información adicional de Apple:

*Si está creando una aplicación del lado del cliente utilizando API de red de alto nivel, como los módulos NSURLSession y CFNetwork, y se conecta con el nombre, no debe alterar ningún elemento para permitir que la aplicación funcione con direcciones IPv6.* Para obtener más información, consulte [Compatibilidad con redes IPv6 DNS64/NAT64](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).

## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### ¿Qué son las métricas del ciclo vital?

Las métricas del ciclo vital son métricas “listas para usar” que se recopilan automáticamente cuando el SDK se implementa por primera vez en la aplicación.

### ¿Cómo puedo solucionar problemas relacionados con las reglas de procesamiento?

Consulte [Consejos y sugerencias de reglas de procesamiento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html) en la documentación de Adobe Analytics.

### ¿Puedo enviar mis datos de análisis a varios grupos de informes?

Sí. Los SDK permiten enviar datos a varios grupos de informes de Adobe Analytics. Para capturar datos de varios grupos de informes usando una solicitud de imagen, defina todos los ID de estos grupos en el campo **[!UICONTROL rsids]** de la sección **[!UICONTROL Analytics]** en el archivo `ADBMobileConfig.json` separados por comas sin espacios.

### ¿En qué se diferencian las visitas de Mobile de los lanzamientos?

El SDK mide un inicio cuando un usuario abre la aplicación por primera vez o regresa a la aplicación después de haber estado fuera durante más tiempo que el valor de tiempo de espera especificado. El tiempo de espera habitual es de 5 minutos (300 segundos) en el campo **[!UICONTROL lifecycleTimeout]**, que está en el archivo `ADBMobileConfig.json`. Una visita es un cálculo del lado del servidor realizado por Adobe Analytics y se basa en las primeras y últimas visitas de datos enviadas por el SDK sin superar el tiempo de espera de visita. Normalmente, los tiempos de espera de sesión se establecen en 30 minutos para un grupo de informes. Aunque las visitas proceden de análisis web tradicionales, estas visitas proporcionan una valiosa perspectiva de cómo los usuarios entran y salen de la aplicación.

## Mensajería {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### ¿Existen limitaciones de tamaño o de otro tipo en las notificaciones push?

Los mensajes de notificación push tienen un límite de 140 caracteres. No hay límites en cuanto a la cantidad de notificaciones que se pueden enviar o programar, o a la frecuencia con que se envían.

### ¿Admite cargas útiles personalizadas para las notificaciones push?

Sí, se proporciona una carga push útil personalizada que puede codificarse en JSON. Las cargas útiles de Android e iOS están restringidas a 4 KB y 2 KB respectivamente. Estas cargas se envían a la aplicación mediante una notificación push o local. Para obtener más información, consulte [Experience: Mensaje push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### ¿Existen limitaciones de tamaño en los mensajes en la aplicación?

Los mensajes en la aplicación publicados y activos creados en Adobe Mobile Services están alojados en un servidor con una restricción de tamaño de 15 MB por grupo de informes de la aplicación. Aunque esta restricción se aplica al contenido del mensaje y a los recursos alojados con Adobe, no hay restricciones sobre los recursos a los que puede referirse el mensaje en la aplicación en otros hosts o en los de la aplicación.

### ¿Puedo utilizar mi propio HTML para los mensajes en la aplicación?

Sí, se admite HTML personalizado para los mensajes en la aplicación. Para obtener más información, consulte [Experience: Mensaje en la aplicación](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### ¿Qué activadores puedo utilizar para enviar notificaciones push o mensajes en la aplicación?

Los especialistas en marketing pueden elegir cualquier dato o evento de Analytics que se envíe como activador para mostrar mensajes en la aplicación. Los mensajes en la aplicación utilizan activadores que se producen de manera local en el dispositivo. Si se eligen varios activadores, todos deben producirse en la misma visita para que se muestre el mensaje. Para obtener más información, consulte [Experience: Mensaje en la aplicación](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

Los mensajes push se envían utilizando segmentos preexistentes de Adobe Analytics o segmentos personalizados que se pueden crear en datos históricos de Analytics ya recopilados. Para obtener más información, consulte [Experience: Mensaje push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### ¿Por qué aparece un error al escribir el nombre del mensaje en la aplicación, el mensaje push o el vínculo de marketing?

No se puede usar el mismo nombre de mensaje en la aplicación, mensaje push o vínculo de marketing en varias aplicaciones que usen el mismo grupo de informes principal o VRS. Para resolver este problema, escriba otro nombre para el mensaje en la aplicación, el mensaje push o el vínculo de marketing.

## Ubicación {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### ¿Hay algún límite en cuanto a los puntos de interés que puedo tener?

No hay restricciones concretas, pero, para lograr un rendimiento ideal y debido a las restricciones de memoria en el dispositivo del usuario, le recomendamos que cree o cargue un máximo de 5000 puntos de interés.

## Adquisición {#section_B37F1129CD5843E890D0E54179455357}

### ¿Puedo atribuir campañas a actividades en la aplicación?

Sí. Adobe Mobile Services puede ayudarle a crear trucos de marketing que le ayudarán a promocionar y dirigir el tráfico a sus aplicaciones y a enlazar las campañas de adquisición con los análisis y las conversiones en la aplicación. Para obtener más información, consulte [Adquisición](/help/using/acquisition-main/acquisition-main.md).

### ¿Cómo puedo configurar vínculos para adquirir y realizar el seguimiento de nuevos usuarios de la aplicación?

Puede crear vínculos de marketing que dirijan a los usuarios a descargar aplicaciones desde Apple App Store y Google Play. Estos vínculos sirven para atribuir los eventos de éxito a las descargas. Para obtener más información, consulte [Generador de vínculos de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).
