---
description: Esta información le ayuda a realizar una campaña de adquisición Versión 3 de ida y vuelta basada en la huella de un dispositivo mediante un vínculo de marketing.
seo-description: Esta información le ayuda a realizar una campaña de adquisición Versión 3 de ida y vuelta basada en la huella de un dispositivo mediante un vínculo de marketing.
seo-title: Prueba de adquisición V3
solution: Marketing Cloud, Analytics
title: Prueba de adquisición V3
uuid: 89137 ccf -4839-4 b 37-926 e -303 cf 8 e 511 a 5
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Testing V3 acquisition{#testing-v-acquisition}

Esta información le ayuda a realizar una campaña de adquisición Versión 3 de ida y vuelta basada en la huella de un dispositivo mediante un vínculo de marketing.

>[!IMPORTANT]
>
>La adquisición V 3 hace referencia a los vínculos de adquisición que crea con el Generador de adquisición en la interfaz de usuario de Adobe Mobile Services. Para utilizar esta función, debe actualizar el SDK para iOS a la versión 4.6.0 o posterior.

Si la aplicación móvil aún no está en el App Store al crearse el vínculo de campaña, puede seleccionar cualquier aplicación móvil como destino. Esto solo determina a qué aplicación lo redirige el servidor de adquisición después de hacer clic en el vínculo de adquisición, y no afecta a la capacidad para probar el vínculo.

1. Complete las tareas previas necesarias en [Adquisición de aplicación móvil](/help/ios/acquisition-main/acquisition.md).
1. Navigate to the **[!UICONTROL Acquisition Builder]** in the Adobe Mobile Services UI and generate an acquisition campaign URL.

   Por ejemplo:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Si en el vínculo de adquisición hace referencia a aplicaciones tanto Android como iOS, utilice el App Store de Apple como tienda predeterminada.
1. Open the generated link in a desktop browser and go to `https://c00.adobe.com/v3/<appid>/end`.

   Debería ver los datos `contextData` en la respuesta JSON:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   If you do not see `contextData`, or some of it is missing, ensure that the acquisition URL follows the format that is specified in [Create Acquisition Link Manually](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Compruebe que los siguientes ajustes del archivo de configuración son correctos:

   | Configuración | Valor |
   |--- |--- |
   | adquisición | The server should be  `c00.adobe.com`. *`appid`* debe ser igual a *`appid`* en el vínculo de adquisición. |
   | analytics | `referrerTimeout` debería tener un valor mayor que 0. |


1. (Condicional) Si el ajuste `ssl` en el archivo de configuración de la aplicación está establecido en true, actualice el vínculo de adquisición para que utilice el protocolo HTTPS.
1. Haga clic en el vínculo generado desde el dispositivo móvil en el que desea instalar la aplicación.

   Los servidores de Adobe (`c00.adobe.com`) almacenan la huella digital y redirigen al App Store. No es necesario descargar la aplicación para realizar pruebas.
1. Inicie la aplicación por primera vez desde el mismo dispositivo móvil utilizado en el paso 6.

   Puede eliminar la aplicación y volver a instalarla, si es necesario.
1. (Opcional) Puede habilitar el registro de la depuración del SDK para obtener información adicional.

   Si todo funciona correctamente, debería ver los siguientes registros:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Si no ve los registros anteriores, asegúrese de que ha completado los pasos 4 y 5.

   A continuación encontrará información sobre posibles errores:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`
Se ha producido un error de red.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      La respuesta no tiene el formato correcto.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      No hay parámetro `contextData` en la respuesta.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` no se incluye `contextData`en.

   * `Analytics - Acquisition referrer timed out`

      No se obtuvo la respuesta en el tiempo definido por `referrerTimeout`. Aumente el valor e inténtelo de nuevo. También debe asegurarse de que ha abierto el vínculo de adquisición antes de instalar la aplicación, y de que utiliza la misma red al hacer clic en la URL y al abrir la aplicación.

      Recuerde la información siguiente:

      * El servidor de adquisición proporciona una coincidencia de atribución basada en la dirección IP y en la información de usuario-agente que se registra al hacer clic en vínculo (paso 6) y al iniciarse la aplicación (paso 7).

         Debe estar en la misma red al hacer clic en la URL y al abrir la aplicación.

      * Mediante herramientas de monitoreado HTTP, las visitas enviadas desde la aplicación pueden monitorearse para verificar la atribución de adquisición.

         You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request sent to the acquisition server. Cualquier variación en el usuario-agente enviado puede provocar el fallo de la atribución.

         >[!TIP]
         >
         >Asegúrese de que `https://c00.adobe.com/v3/<appid>/start` y `https://c00.adobe.com/v3/<appid>/end` tiene los mismos valores de usuario-agente.

      * El vínculo de adquisición y la visita del SDK deben utilizar el mismo protocolo (HTTP o HTTPS).

         En caso contrario (por ejemplo, si el vínculo utiliza HTTP y el SDK utiliza HTTPS), las direcciones IP podrían diferir para cada solicitud (en algunos operadores) y la atribución podría fallar.
