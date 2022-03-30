---
description: Esta información le ayuda a realizar una campaña de adquisición Versión 3 de ida y vuelta basada en la huella de un dispositivo mediante un vínculo de marketing.
solution: Experience Cloud Services,Analytics
title: Prueba de adquisición V3
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
exl-id: 3cf66802-1f2c-428f-86ef-a9afc57e3470
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 100%

---

# Prueba de adquisición V3 {#testing-v-acquisition}

Esta información le ayuda a realizar una campaña de adquisición Versión 3 de ida y vuelta basada en la huella de un dispositivo mediante un vínculo de marketing.

>[!IMPORTANT]
>
>Adquisición V3 se refiere a los vínculos de adquisición que crea con el Generador de adquisición en la interfaz de usuario de Adobe Mobile Services. Para utilizar esta función, debe actualizar al iOS de SDK versión 4.6.0 o posterior.

Si la aplicación móvil aún no está en la App Store, al crear el vínculo de campaña, seleccione cualquier aplicación móvil como destino. Esto solo afecta a la aplicación a la que el servidor de adquisición le redirige después de hacer clic en el vínculo de adquisición, pero no afecta a la capacidad de probar el vínculo.

1. Complete las tareas previas necesarias en [Adquisición de aplicación móvil](/help/ios/acquisition-main/acquisition.md).
1. Vaya al **[!UICONTROL Generador de adquisición]** en la interfaz de usuario de Adobe Mobile Services y genere una URL de campaña de adquisición.

   Por ejemplo:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Si en el vínculo de adquisición hace referencia a aplicaciones de iOS y Android, utilice la Apple Store como tienda predeterminada.
1. Abra el vínculo generado en un explorador de escritorio y vaya a `https://c00.adobe.com/v3/<appid>/end`.

   Debería ver los datos `contextData` en la respuesta JSON:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   Si no ve `contextData`, o si falta parte de la cadena, asegúrese de que la URL de adquisición sigue el formato indicado en [Crear vínculo de adquisición manualmente](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Compruebe que los siguientes ajustes del archivo de configuración son correctos:

   | Configuración | Valor |
   |--- |--- |
   | adquisición | El servidor debe ser `c00.adobe.com`. El *`appid`* debe coincidir con el *`appid`* del vínculo de adquisición. |
   | analytics | `referrerTimeout` debería tener un valor mayor que 0. |


1. (Condicional) Si el ajuste `ssl` en el archivo de configuración de la aplicación está establecido en true, actualice el vínculo de adquisición para que utilice el protocolo HTTPS.
1. Haga clic en el vínculo generado desde el dispositivo móvil en el que quiere a instalar la aplicación.

   Los servidores de Adobe (`c00.adobe.com`) almacenan la huella digital y redirigen al App Store. No es necesario descargar la aplicación para realizar pruebas.
1. Inicie la aplicación por primera vez desde el mismo dispositivo móvil utilizado en el paso 6.

   Puede eliminar la aplicación y volver a instalarla, si es necesario.
1. (Opcional) Puede habilitar el registro de la depuración del SDK para obtener información adicional.

   Si todo funciona correctamente, debería ver los siguientes registros:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Si no ve los registros anteriores, asegúrese de haber completado los pasos 4 y 5.

   A continuación se ofrece información sobre posibles errores:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`
Se ha producido un error de red.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      La respuesta no tiene el formato correcto.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      No hay parámetro `contextData` en la respuesta.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` no se incluye en `contextData`.

   * `Analytics - Acquisition referrer timed out`

      No se obtuvo la respuesta en el tiempo definido por `referrerTimeout`. Aumente el valor e inténtelo de nuevo. También debe asegurarse de que ha abierto el vínculo de adquisición antes de instalar la aplicación y de que está utilizando la misma red al hacer clic en la URL y al abrir la aplicación.

      Recuerde la información siguiente:

      * El servidor de adquisición proporciona una coincidencia de atribución basada en la dirección IP y en la información de usuario-agente que se registra al hacer clic en vínculo (paso 6) y al iniciarse la aplicación (paso 7).

         Debe estar en la misma red al hacer clic en la URL y al abrir la aplicación.

      * Mediante herramientas de monitorización HTTP, las visitas enviadas desde la aplicación pueden monitorizarse para verificar la atribución de adquisición.

         Debería ver una solicitud de `/v3/<appid>/start` y una solicitud de `/v3/<appid>/end` que se han enviado al servidor de adquisición. Cualquier variación en el usuario-agente enviado puede provocar el fallo de la atribución.

         >[!TIP]
         >
         >Asegúrese de que `https://c00.adobe.com/v3/<appid>/start` y `https://c00.adobe.com/v3/<appid>/end` tengan los mismos valores de usuario-agente.

      * El vínculo de adquisición y la visita del SDK deben utilizar el mismo protocolo (HTTP o HTTPS).

         En caso contrario (por ejemplo, si el vínculo utiliza HTTP y el SDK utiliza HTTPS), las direcciones IP podrían diferir para cada solicitud (en algunos operadores) y la atribución podría fallar.
