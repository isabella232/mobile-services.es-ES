---
description: Las siguientes instrucciones le ayudan a realizar una campaña de adquisición de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.
keywords: android;library;mobile;sdk
seo-description: Las siguientes instrucciones le ayudan a realizar una campaña de adquisición de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.
seo-title: Prueba de adquisición de vínculos de marketing
solution: Experience Cloud,Analytics
title: Prueba de adquisición de vínculos de marketing
topic: Developer and implementation
uuid: d0933dcc-8fc3-4f60-987f-7a54559aacf5
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 100%

---


# Prueba de adquisición de vínculos de marketing {#testing-marketing-link-acquisition}

Las siguientes instrucciones le ayudan a realizar una campaña de adquisición de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.

Si su aplicación móvil aún no está en Google Play, puede seleccionar cualquier aplicación móvil como destino al crear el vínculo de marketing. Esto solo determina a qué aplicación lo redirige el servidor de adquisición después de hacer clic en el vínculo de adquisición, y no afecta la capacidad para probar el vínculo. Los parámetros de cadena de consulta se pasan a la tienda Google Play que pasan a la aplicación durante la instalación como parte de una difusión de campaña. La prueba de adquisición de aplicaciones móviles de ida y vuelta requiere la simulación de este tipo de difusión.

Las pruebas siempre se deben realizar con la aplicación recién instalada, o después de borrar sus datos desde la **[!UICONTROL Configuración]**. Así se garantiza el envío durante el primer inicio de las métricas del ciclo vital iniciales asociadas a los parámetros de la cadena de consulta de la campaña.

1. Complete las tareas previas en [Adquisición de aplicaciones móviles](/help/android/acquisition-main/acquisition.md) y asegúrese de que ha implementado correctamente el receptor de difusión de `INSTALL_REFERRER`.
1. En la interfaz de usuario de Adobe Mobile Services, haga clic en **[!UICONTROL Adquisición]** > **[!UICONTROL Generador de vínculos de marketing]** y cree un vínculo URL de marketing de adquisición que establezca Google Play como destino para dispositivos Android.

   Para obtener más información, consulte [Generador de vínculos de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Por ejemplo:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Abra en el dispositivo Android el vínculo generado.

   Se le debería redirigir a una página con una dirección URL similar a la del siguiente ejemplo:

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copie el ID exclusivo después de `utm_content%3D`.

   En el ejemplo anterior, el ID es `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

   Si no puede obtener el ID exclusivo en el dispositivo, ejecute el siguiente comando `CURL` en el equipo de escritorio para obtener el ID exclusivo de la cadena de respuesta.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Por ejemplo:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Construya el vínculo de fin de adquisición utilizando el identificador exclusivo del paso 3, empleando el siguiente formato:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   Por ejemplo, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Abra el vínculo en un navegador.

   Debería ver `contextData` en la respuesta JSON:

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. Repita el paso 3 para obtener un nuevo ID exclusivo.
1. Compruebe que los siguientes ajustes del archivo de configuración son correctos:

   | Configuración | Valor |
   |--- |--- |
   | adquisición | El servidor debe ser `c00.adobe.com`, y *`appid`*  debe coincidir con el `appid` del vínculo de adquisición. |
   | analytics | Para hacer pruebas, establezca el tiempo de espera de remitente del reenvío para permitir que el tiempo de envío manual (60 segundos o más) de la difusión sea el adecuado. Puede restaurar la configuración de tiempo de espera original después de hacer la prueba. |

1. Conecte el dispositivo a un equipo, desinstale e instale de nuevo la aplicación.
1. Inicie ADB Shell e inicie la aplicación en el dispositivo.

   ```
   adb shell
   ```

1. Envíe una emisión utilizando el siguiente comando `adb`:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. Reemplace `com.adobe.android` por el nombre del paquete de su aplicación, actualice en su aplicación la referencia del receptor con la referencia de la ubicación del receptor de seguimiento de la campaña y reemplace los valores que estén asociados a `utm_content`.

   Si la emisión se realiza correctamente, recibirá una respuesta similar al siguiente ejemplo:

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (Opcional) Puede habilitar el registro de la depuración del SDK para obtener información adicional.

   Si todo funciona correctamente, debería ver los siguientes registros:

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   Si no ve estos registros, compruebe si ha completado los pasos del 6 al 10.

   La siguiente tabla contiene información adicional sobre los posibles errores:

   | Error | Descripción |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | El formato de la respuesta no es correcto. |
   | Analytics - Unable to parse response (`a JSON Response`). | El formato de la cadena JSON no es correcto. |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | No hay parámetro `contextData` en la respuesta. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` no se incluye en contextData. |
   | Analytics - Acquisition referrer timed out. | No se obtuvo la respuesta en el tiempo definido por `referrerTimeout`. Aumente el valor e inténtelo de nuevo.  También debe asegurarse de haber abierto el vínculo de adquisición antes de instalar la aplicación. |

Recuerde la información siguiente:

* Las visitas que se envían desde la aplicación se pueden supervisar mediante herramientas de supervisión HTTP para verificar la atribución de adquisición.
* Para obtener más información acerca de cómo emitir `INSTALL_REFERRER`, consulte [Prueba de medición de campaña de Google Play](https://developers.google.com/analytics/solutions/testing-play-campaigns) en la Guía para desarrolladores de Google.
* Puede utilizar la herramienta Java `acquisitionTest.jar` que se proporciona para ayudarle a obtener el identificador exclusivo y el referente de instalación de emisión, lo que a su vez le ayuda a obtener la información en los pasos 3 al 10.

**Instalación de la herramienta Java**

Para instalar la herramienta Java:

1. Descargue el archivo [`acquistionTester.zip`](../assets/acquisitionTester.zip).
1. Extraiga el archivo .jar.

   Puede ejecutar el archivo .jar en la línea de comandos.

Por ejemplo:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

Los vínculos de marketing se guardan en la memoria caché del servidor con una caducidad de 10 minutos. Cuando realice cambios en los vínculos de marketing, antes de poder usar los vínculos de nuevo espere unos 10 minutos para que los cambios entren en vigor.
