---
description: Las siguientes instrucciones le ayudan a realizar una campaña de adquisición con un vínculo de marketing basado en una huella de dispositivo.
keywords: android; library; mobile; sdk
seo-description: Las siguientes instrucciones le ayudan a realizar una campaña de adquisición con un vínculo de marketing basado en una huella de dispositivo.
seo-title: Prueba de adquisición de vínculo de marketing
solution: Marketing Cloud, Analytics
title: Prueba de adquisición de vínculo de marketing
topic: Desarrollador e implementación
uuid: 69503 e 01-182 d -44 c 6-b 0 fb-e 1 c 012 ffa 3 bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

Las siguientes instrucciones le ayudan a realizar una campaña de adquisición con un vínculo de marketing basado en una huella de dispositivo.

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
   | adquisición | The server should be  `c00.adobe.com`. `appid` debe ser igual a *`appid`* en el vínculo de adquisición. |
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

   Si no ve estos registros, verifique que ha completado los pasos 4 y 5.

   A continuación encontrará información sobre posibles errores:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

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

* El servidor de adquisición proporciona una coincidencia de atribución basada en la dirección IP y en la información de usuario-agente que se registró al hacer clic en vínculo (paso 6) y al iniciarse la aplicación (paso 7).

   Debe estar en la misma red al hacer clic en la URL y al abrir la aplicación.

* Mediante herramientas de monitoreado HTTP, las visitas enviadas desde la aplicación pueden monitorearse para verificar la atribución de adquisición.

   You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request that are sent to the acquisition server.

* Cualquier variación en el usuario-agente enviado puede provocar el fallo de la atribución.

   Asegúrese de que `https://c00.adobe.com/v3/<appid>/start` y `https://c00.adobe.com/v3/<appid>/end` tiene los mismos valores de usuario-agente.

* El vínculo de adquisición y la visita del SDK deben utilizar el mismo protocolo (HTTP o HTTPS).

   Si el vínculo y la visita utilizan protocolos diferentes, por ejemplo, el vínculo utiliza HTTP y el SDK utiliza HTTPS, la dirección IP puede diferir en algunos operadores para cada solicitud. Esto podría provocar el fallo de la atribución.

* Los vínculos de marketing se almacenan en caché en el servidor con un tiempo de caducidad de diez minutos.

   Cuando realice cambios en Vínculos de marketing, debe esperar unos 10 minutos antes de utilizar los vínculos.