---
description: Preguntas más frecuentes y respuestas sobre Adobe Mobile Services, además de una descripción general de las funciones.
keywords: móvil
seo-description: Preguntas más frecuentes y respuestas sobre Adobe Mobile Services, además de una descripción general de las funciones.
seo-title: Preguntas frecuentes
solution: Marketing Cloud,Analytics
title: Preguntas frecuentes
topic: Métricas
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Preguntas frecuentes {#frequently-asked-questions}

La siguiente tabla contiene una lista de las preguntas más frecuentes sobre Adobe Mobile Services:

## SDK de Adobe Mobile {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### ¿El SDK se actualiza frecuentemente?

Sí, constantemente realizamos actualizaciones y nos esforzamos en ofrecer los SDK más funcionales, compatibles con los estándares y seguros. Normalmente, se lanza una nueva versión todos los meses. Estas actualizaciones de SDK son sustitutos automáticos (para la versión 4x) que ayudan a facilitar la implementación. Para obtener más información sobre nuestras actualizaciones, consulte las [Notas de la versión](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### ¿Qué versión del SDK debería tener?

La versión actual del SDK es 4.11. Para obtener más información, consulte las [Notas de la versión](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### ¿Dónde puedo descargar los SDK?

Los SDK para plataformas móviles individuales se pueden descargar desde la sección [Administrar configuración](/help/using/c-manage-app-settings/c-manage-app-settings.md) de aplicación.

### ¿Cómo configuro los SDK?

After you create a new app report suite, navigate to Manage App Settings and configure all of the required options on the app information page. Una vez guardada la configuración, descargue los SDK necesarios desde la parte inferior de la página Administrar configuración de aplicación. The SDK will come pre-configured with the options you have saved and can be found in the `ADBMobileConfig.json` file in the SDK package. If you change any SDK settings on the Manage App Settings page, make sure you re-download the SDK files or update your `ADBMobileConfig.json` file with the necessary changes.

### ¿Los SDK de Adobe Mobile admiten IPv6 para iOS?

Los SDK de Adobe Mobile utilizan las pilas de red de iOS y Android estándar. For iOS, the SDK uses NSURLSession (iOS versions 7+) and NSURLConnection (iOS versions 7 and later) which are fully compliant with IPv6. Es posible que los desarrolladores que hayan creado o utilizado su propia pila de redes deseen revisar si existen otras consideraciones que los mitiguen. A continuación se muestra información adicional de Apple:

*If you're writing a client-side app using high-level networking APIs such as NSURLSession and the CFNetwork frameworks and you connect by name, you should not need to change anything for your app to work with IPv6 addresses.* Para obtener más información, consulte [Compatibilidad con redes](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1)IPv6 DNS64/NAT64.


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### ¿Qué son las Métricas del ciclo vital?

Las Métricas del ciclo vital son métricas originales que se recopilan automáticamente cuando el SDK se implementa por primera vez en la aplicación. For more information, see [Lifecycle Metrics (Android)](/help/android/metrics.md) and [Lifecycle Metrics (iOS)](/help/ios/metrics.md).

### ¿Cómo puedo solucionar problemas relacionados con las reglas de procesamiento?

Para obtener más información, consulte [Consejos y sugerencias de reglas de procesamiento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html).

### ¿Puedo enviar mis datos de Analytics a varios grupos de informes?

Sí. Los SDK proporcionan la posibilidad de enviar datos a varios grupos de informes de Adobe Analytics. Para capturar datos de varios grupos de informes usando una solicitud de imagen, defina todos los ID de estos grupos en el campo **[!UICONTROL rsids]** de la sección **Analytics[!UICONTROL en el archivo separados por comas sin espacios.]**`ADBMobileConfig.json` Para obtener más información, consulte [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md).

### ¿En qué se diferencian las visitas de Mobile de los inicios?

El SDK mide un inicio cuando un usuario abre la aplicación por primera vez o vuelve a la aplicación después de haber estado fuera durante un tiempo superior al valor especificado como tiempo de espera. The typical timeout is 5 minutes (300 seconds) in **[!UICONTROL lifecycleTimeout]** field, which is located in the `ADBMobileConfig.json` file. Una visita es un cálculo del lado del servidor realizado en Adobe Analytics que se basa en las primeras y últimas visitas de datos que el SDK envía sin superar un tiempo de espera de visita. Normalmente, el tiempo de espera de la sesión se establece en 30 minutos para un grupo de informes. Aunque las visitas proceden de análisis web tradicionales, estas visitas también proporcionan importantes datos sobre cómo los usuarios entran y salen de una aplicación.

## Mensajería {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### ¿Hay limitaciones de tamaño o de otro tipo sobre las notificaciones push?

Los mensajes de notificación push tienen un límite de 140 caracteres. No hay límite en cuanto al número de notificaciones que se pueden enviar o programar o sobre la frecuencia de envío.

### ¿Se admiten las cargas útiles personalizadas para las notificaciones push?

Sí, proporcionamos una carga útil push personalizada que se puede codificar en JSON. Las cargas útiles de Android e iOS están restringidas a 4 KB y 2 KB respectivamente. Estas cargas útiles se envían a la aplicación mediante una notificación push o local. For more information, see [Experience: Push Message](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### ¿Hay limitaciones de tamaño en los mensajes en la aplicación?

Los mensajes en la aplicación publicados y activos creados en Adobe Mobile Services se albergan en un servidor con una restricción de 15 MB por grupo de informes de la aplicación. Mientras que esta restricción se aplica al contenido del mensaje y a los recursos albergados con Adobe, no hay restricciones en cuanto a que esos recursos del mensaje en la aplicación puedan referirse a otros hosts o a los existentes en la aplicación.

### ¿Puedo utilizar mi propio HTML para los mensajes en la aplicación?

Sí, se admite el HTML personalizado para los mensajes en la aplicación. For more information, see [Experience: In-App Message](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### ¿Qué activadores puedo utilizar para enviar notificaciones push o mensajes en la aplicación?

Los especialistas en marketing pueden elegir cualquier dato o evento de Analytics como activador para mostrar mensajes en la aplicación. Los mensajes en la aplicación utilizan activadores que se producen localmente en el dispositivo. Si se eligen varios activadores, para que se muestre el mensaje, todos se deben producir en la misma visita. Para obtener más información, consulte [Experiencia: mensaje en la aplicación](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

Los mensajes push se envían utilizando segmentos preexistentes de Adobe Analytics o segmentos personalizados que se pueden crear en datos históricos de Analytics ya recopilados. Para obtener más información, consulte [Experiencia: Mensaje push](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### ¿Por qué se produce un error con el nombre en la aplicación, push o vínculo de marketing que he escrito?

No se puede usar el mismo nombre de mensaje en la aplicación, mensaje push o vínculo de marketing en varias aplicaciones que usen el mismo grupo de informes principal o VRS. Para resolver este problema, escriba otro nombre para el mensaje en la aplicación, el mensaje push o el vínculo de marketing.

## Ubicación {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Is there a limit on how many oints of interest (POIs) I can have?

No hay restricciones concretas, pero, para lograr un rendimiento ideal y debido a las restricciones de memoria en el dispositivo del usuario, le recomendamos que cree o cargue un máximo de 5000 puntos de interés.

## Adquisición {#section_B37F1129CD5843E890D0E54179455357}

### ¿Puedo atribuir campañas a actividades en la aplicación?

Sí. Adobe Mobile Services puede ayudarle a crear trucos de marketing que ayuden a promover y llevar el tráfico a sus aplicaciones, y a vincular campañas de adquisición con análisis y conversiones en la aplicación. Para obtener más información, consulte [Adquisición](/help/using/acquisition-main/acquisition-main.md).

### ¿Cómo puedo configurar vínculos para adquirir y realizar el seguimiento de nuevos usuarios de la aplicación?

You can create Marketing Links that route users to download applications from the Apple App Store and Google Play. Estos vínculos sirven para atribuir los eventos de éxito a las descargas. Para obtener más información, consulte [Generador de vínculos de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).