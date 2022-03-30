---
description: Esta información le ayuda a utilizar el SDK para Android con Adobe Analytics.
keywords: android, biblioteca, mobile, móvil, sdk
solution: Experience Cloud Services,Analytics
title: Información general de Analytics
topic-fix: Developer and implementation
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
exl-id: ed9f55e6-f3ab-4c1e-9a2f-1ee67a7b4c03
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 95%

---

# Información general de Analytics {#analytics}

Esta información le ayuda a utilizar el SDK para Android con Adobe Analytics.

## Nueva versión del SDK móvil de Adobe Experience Platform

¿Busca información y documentación relacionada con el SDK móvil de Adobe Experience Platform? Haga clic [aquí](https://aep-sdks.gitbook.io/docs/) para obtener la documentación más reciente.

En septiembre de 2018, publicamos una nueva versión principal del SDK. Estos nuevos SDK móviles de la Adobe Experience Platform se pueden configurar a través de [Experience Platform Launch](https://www.adobe.com/es/experience-platform/launch.html).

* Para empezar, vaya a Adobe Experience Platform Launch.
* Para ver el contenido de los repositorios del SDK de la plataforma Experience, vaya a [Github: SDK de la Adobe Experience Platform](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Generar identificadores de seguimiento de Analytics

En los SDK, los identificadores se utilizan para rastrear usuarios y aquí está la jerarquía de identificadores:

1. Identificador de visitante personalizado (VID)
1. Identificador de seguimiento de Analytics (AID)
1. Identificador de Experience Cloud (MID)

>[!TIP]
>
>El acrónimo correcto del Identificador de Experience Cloud es ECID. Aunque los SDK todavía usan MID, es el acrónimo antiguo.

El SDK genera el AID, que a veces también se denomina Identificador de seguimiento, cuando la aplicación no está configurada para utilizar una MID. El valor persiste entre inicios y actualizaciones de aplicaciones en `SharedPreferences`. Si el usuario elimina la aplicación de su dispositivo y luego la reinstala, o si el desarrollador de la aplicación elimina SharedPreferences, el SDK genera un nuevo identificador. Este proceso genera un nuevo usuario en el sistema de informes de Analytics.

Para los usuarios de una aplicación que introduce la compatibilidad con el servicio de identidad (MID), los valores de AID existentes se envían con las visitas de Analytics, y la visita de Analytics contiene un AID y un MID. Para los usuarios nuevos de una aplicación con compatibilidad con el servicio de identidad, las solicitudes de Analytics solo contienen un MID. Para obtener más información sobre la identificación de visitantes, consulte [Visitantes únicos](https://experienceleague.adobe.com/docs/analytics/components/metrics/unique-visitors.html?lang=es) en la documentación de Adobe Analytics.
