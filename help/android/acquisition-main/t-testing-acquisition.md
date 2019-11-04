---
description: La siguiente información le ayuda a realizar una adquisición de elementos heredados de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: La siguiente información le ayuda a realizar una adquisición de elementos heredados de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.
seo-title: Prueba de adquisición de elementos heredados
solution: Experience Cloud,Analytics
title: Prueba de adquisición de elementos heredados
topic: Desarrollador e implementación
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Prueba de adquisición de elementos heredados {#testing-legacy-acquisition}

La siguiente información le ayuda a realizar una adquisición de elementos heredados de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.

Si la aplicación móvil aún no está en Google Play, puede seleccionar cualquier aplicación móvil como destino al crear el vínculo de campaña. Esto solo afecta a la aplicación a la que lo redirige el servidor de adquisición, después de hacer clic en el vínculo de adquisición, pero no a la capacidad para probar el vínculo de adquisición. Los parámetros de cadena de la consulta se pasan a la tienda Google Play y luego a la aplicación durante la instalación, como parte de una emisión de campaña. La prueba de adquisición de aplicación móvil de ida y vuelta requiere simular este tipo de emisión.

Las pruebas siempre se deben realizar con la aplicación recién instalada, o después de borrar sus datos desde la **[!UICONTROL Configuración]**. Así se garantiza el envío durante el primer inicio de las métricas del ciclo vital iniciales asociadas a los parámetros de la cadena de consulta de la campaña.

1. En la interfaz de usuario de Mobile Services, genere una URL de campaña de adquisición de elementos heredados.

   Para obtener más información, consulte [Uso de vínculos de adquisición de elementos heredados](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Conecte el dispositivo a un equipo, inicie ADB Shell y luego inicie la aplicación en el dispositivo.
1. Envíe una emisión utilizando el siguiente formato:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Complete los pasos siguientes:
   1. Sustituya `com.example.adobetesttapp.com` por la entrada DNS inversa de su aplicación.
   1. Actualice en la aplicación la referencia del receptor con la referencia de la ubicación del receptor de seguimiento de la campaña.
   1. Reemplace por valores apropiados los que estén asociados a `utm_content`, `utm_source`, `utm_campaign`, `utm_medium`, `utm_term`, etc.

Si la emisión se realiza correctamente, se muestra una respuesta similar a la de abajo:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

También verá que se ha enviado una solicitud de imagen a los servidores de recopilación de datos de Adobe. Si el SDK consume todo el tiempo de espera del referente (establecido en el paso 1) con una solicitud de imagen que no incluye parámetros de campaña, la emisión falla.
