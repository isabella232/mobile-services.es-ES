---
description: La siguiente información le ayuda a realizar una adquisición de elementos heredados de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.
keywords: android; library; mobile; sdk
seo-description: La siguiente información le ayuda a realizar una adquisición de elementos heredados de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.
seo-title: Prueba de adquisición de elementos heredados
solution: Marketing Cloud, Analytics
title: Prueba de adquisición de elementos heredados
topic: Desarrollador e implementación
uuid: bb 7 ace 96-68 eb -4 f 43-b 3 cf-af 80730 b 9 cee
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Testing legacy acquisition {#testing-legacy-acquisition}

La siguiente información le ayuda a realizar una adquisición de elementos heredados de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.

Si la aplicación móvil aún no está en Google Play, puede seleccionar cualquier aplicación móvil como destino al crear el vínculo de campaña. Esto solo afecta a la aplicación a la que lo redirige el servidor de adquisición, después de hacer clic en el vínculo de adquisición, pero no a la capacidad para probar el vínculo de adquisición. Los parámetros de cadena de la consulta se pasan a la tienda Google Play y luego a la aplicación durante la instalación, como parte de una emisión de campaña. La prueba de adquisición de aplicación móvil de ida y vuelta requiere simular este tipo de emisión.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. Así se garantiza el envío durante el primer inicio de las métricas del ciclo vital iniciales asociadas a los parámetros de la cadena de consulta de la campaña.

1. En la interfaz de usuario de Mobile Services, genere una URL de campaña de adquisición de elementos heredados.

   For more information, see [Use legacy Acquisition links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Conecte el dispositivo a un equipo, inicie ADB Shell y luego inicie la aplicación en el dispositivo.
1. Envíe una emisión utilizando el siguiente formato:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Complete los pasos siguientes:
   1. Sustituya `com.example.adobetesttapp.com` por la entrada DNS inversa de su aplicación.
   1. Actualice en la aplicación la referencia del receptor con la referencia de la ubicación del receptor de seguimiento de la campaña.
   1. Replace values that are associated with `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, and so on, with appropriate values.

Si la emisión se realiza correctamente, se muestra una respuesta similar a la de abajo:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

También verá que se ha enviado una solicitud de imagen a los servidores de recopilación de datos de Adobe. Si el SDK consume todo el tiempo de espera del referente (establecido en el paso 1) con una solicitud de imagen que no incluye parámetros de campaña, la emisión falla.