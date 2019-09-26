---
description: The following instructions help you roundtrip an acquisition campaign with a Marketing Link that is based on a device fingerprint.
keywords: android;library;mobile;sdk
seo-description: Las siguientes instrucciones le ayudan a realizar una campaña de adquisición de ida y vuelta con un vínculo de marketing basado en la huella de un dispositivo.
seo-title: Prueba de adquisición de vínculos de marketing
solution: Marketing Cloud,Analytics
title: Prueba de adquisición de vínculos de marketing
topic: Desarrollador e implementación
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

Las siguientes instrucciones le ayudan a realizar una campaña de adquisición de ida y vuelta con un vínculo de marketing basado en la huella de un dispositivo.

1. Complete las tareas previas necesarias en [Adquisición de aplicación móvil](/help/ios/acquisition-main/acquisition.md).
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   Por ejemplo:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Para obtener más información, consulte [Generador de vínculos de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   Debería ver contextData en la respuesta JSON:

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Compruebe que los siguientes ajustes del archivo de configuración son correctos:

   | Configuración | Valor |
   |--- |--- |
   | acquisition | The server should be  `c00.adobe.com`. `appid` should equal the  *`appid`* in your acquisition link. |
   | analytics | `referrerTimeout` debería tener un valor mayor que 0. |

1. (Condicional) Si el ajuste SSL en el archivo de configuración de la aplicación está establecido en `false`, actualice el vínculo de adquisición para que utilice el protocolo HTTP en lugar de HTTPS.
1. Haga clic en el vínculo generado desde el dispositivo móvil en el que quiere a instalar la aplicación.

   Los servidores de Adobe (`c00.adobe.com`) almacenan la huella digital y redirigen al App Store. No es necesario descargar la aplicación para realizar pruebas.
1. Inicie la aplicación por primera vez desde el mismo dispositivo móvil utilizado en el paso 6.

   Puede eliminar la aplicación y volver a instalarla, si es necesario.
1. (Opcional) Habilite el registro de la depuración del SDK para obtener información adicional.

   Si todo funciona correctamente, debería ver los siguientes registros:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   If you do not see these logs, verify that you completed steps 4 and 5.

   Here is some information about possible errors:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      Se ha producido un error de red.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      La respuesta no tiene el formato correcto.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      No hay parámetro `contextData` en la respuesta.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` is not included in `contextData`.

   * `Analytics - Acquisition referrer timed out`

      No se obtuvo la respuesta en el tiempo definido por `referrerTimeout`. Aumente el valor e inténtelo de nuevo. También debe asegurarse de que ha abierto el vínculo de adquisición antes de instalar la aplicación, y de que utiliza la misma red al hacer clic en la URL y al abrir la aplicación.

Recuerde la información siguiente:

* El servidor de adquisición proporciona una coincidencia de atribución basada en la dirección IP y en la información de usuario-agente que se registró al hacer clic en vínculo (paso 6) y al iniciarse la aplicación (paso 7).

   Debe estar en la misma red al hacer clic en la URL y al abrir la aplicación.

* Mediante herramientas de monitoreado HTTP, las visitas enviadas desde la aplicación pueden monitorizarse para verificar la atribución de adquisición.

   Debería ver una solicitud de `/v3/<appid>/start` y una solicitud de `/v3/<appid>/end` que se han enviado al servidor de adquisición.

* Cualquier variación en el usuario-agente enviado puede provocar el fallo de la atribución.

   Ensure that  and  have the same user-agent values.`https://c00.adobe.com/v3/<appid>/start``https://c00.adobe.com/v3/<appid>/end`

* El vínculo de adquisición y la visita del SDK deben utilizar el mismo protocolo (HTTP o HTTPS).

   Si el vínculo y la visita están utilizando diferentes protocolos, donde por ejemplo, el vínculo utiliza HTTP y el SDK utiliza HTTPS, la dirección IP puede diferir en algunos operadores para cada solicitud. Esto podría provocar el fallo de la atribución.

* The Marketing Links are cached on the server side with a ten-minutes expiration time.

   When you make changes to Marketing Links, you should wait about 10 minutes before using the links.