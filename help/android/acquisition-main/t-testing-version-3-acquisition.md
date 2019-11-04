---
description: Esta información le ayuda a realizar una adquisición Versión 3 de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Esta información le ayuda a realizar una adquisición Versión 3 de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.
seo-title: Prueba de adquisición Versión 3
solution: Experience Cloud,Analytics
title: Prueba de adquisición Versión 3
topic: Desarrollador e implementación
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: ht
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Prueba de adquisición V3{#testing-version-acquisition}

Esta información le ayuda a realizar una adquisición Versión 3 de ida y vuelta en un dispositivo Android mediante un vínculo de marketing.

>[!IMPORTANT]
>
>La función de adquisición en la versión 3 se refiere a los vínculos de adquisición que crea con el Generador de adquisiciones en la interfaz de usuario de Adobe Mobile Services. Para usar esta función, debe efectuar la actualización al SDK para Android 4.x para soluciones de Experience Cloud 4.6.0 o versiones posteriores.

Si la aplicación móvil aún no está en Google Play al crearse el vínculo de campaña, puede seleccionar cualquier aplicación móvil como destino. Esto solo determina a qué aplicación lo redirige el servidor de adquisición después de hacer clic en el vínculo de adquisición, y no afecta a la capacidad para probar el vínculo. Los parámetros de cadena de la consulta se pasan a la tienda Google Play y luego a la aplicación durante la instalación, como parte de una emisión de campaña. La prueba de adquisición de aplicación móvil de ida y vuelta requiere simular este tipo de emisión.

Las pruebas siempre se deben realizar con la aplicación recién instalada, o después de borrar sus datos desde la **[!UICONTROL Configuración]**. Así se garantiza el envío durante el primer inicio de las métricas del ciclo vital iniciales asociadas a los parámetros de la cadena de consulta de la campaña.

1. Complete las tareas previas en [Adquisición de aplicaciones móviles](/help/android/acquisition-main/acquisition.md) y asegúrese de que ha implementado correctamente el receptor de difusión de `INSTALL_REFERRER`.
1. En la interfaz de usuario de Adobe Mobile Services, haga clic en **[!UICONTROL Adquisición]** &gt; **[!UICONTROL Generador de vínculos de marketing]** y cree un vínculo URL de marketing de adquisición que establezca Google Play como destino para dispositivos Android.

   Para obtener más información, consulte [Generador de vínculos de marketing](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Por ejemplo, `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >Si en el vínculo de adquisición hace referencia a aplicaciones tanto Android como iOS, utilice Google Play como tienda predeterminada.

1. Abra el vínculo generado en un navegador de escritorio.

   Se le debería redirigir a una página con una dirección URL similar a la del siguiente ejemplo:
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Copie el ID exclusivo después de `utm_content%3D`.

   En el ejemplo anterior, el ID es `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Construya el vínculo de fin de adquisición utilizando el ID exclusivo del paso 3, empleando el siguiente formato:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`.

   Por ejemplo, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Abra el vínculo en un navegador de escritorio.

   Debería ver `contextData` en la respuesta JSON:

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   Si no ve `contextData`, o si falta parte de la cadena, asegúrese de que la URL de adquisición sigue el formato indicado en [Crear vínculo de adquisición manualmente](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Repita el paso 3 para obtener un nuevo ID exclusivo.
1. Compruebe que los siguientes ajustes del archivo de configuración son correctos:

   | Configuración | Valor |
   |--- |--- |
   | adquisición | El servidor debe ser `c00.adobe.com`. El *`appid`* debe coincidir con el `appid` del vínculo de adquisición. |
   | analytics | Para realizar pruebas establezca un tiempo de espera del referente adecuado (60 segundos o más) para poder enviar manualmente la emisión. Tras la prueba, puede restablecer la configuración original del tiempo de espera. |

1. Conecte el dispositivo a un equipo, desinstale e instale de nuevo la aplicación.
1. Inicie ADB Shell e inicie la aplicación en el dispositivo.
1. Envíe una emisión utilizando el siguiente comando `adb`:

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. Complete los pasos siguientes:
   1. Reemplace `com.adobe.android` con el nombre del paquete de su aplicación.
   1. Actualice en la aplicación la referencia del receptor con la ubicación del receptor de seguimiento de la campaña
   1. Reemplace los valores asociados con `utm_content`.
   Si la emisión se realiza correctamente, recibirá una respuesta similar al siguiente ejemplo:

   `Broadcasting: Intent 
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
Broadcast completed: result=0`

1. (Opcional) Puede habilitar el registro de la depuración del SDK para obtener información adicional.

   Si todo funciona correctamente, debería ver los siguientes registros:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

Si no ve los registros anteriores, asegúrese de haber completado los pasos 6 al 12.

La siguiente tabla contiene información adicional acerca de los posibles errores:

| Error | Descripción |
|--- |--- |
| Analytics - Unable to decode response(*String*). | El formato de la respuesta no es correcto. |
| Analytics - Unable to parse response (*a JSON Response*). | El formato de la cadena JSON no es correcto. |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | No hay parámetro contextData en la respuesta. |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name`  no se incluye en contextData. |
| Analytics - Acquisition referrer timed out. | No se obtuvo la respuesta en el tiempo definido por `referrerTimeout`. Aumente el valor e inténtelo de nuevo.  Además, debe asegurarse de abrir el vínculo de adquisición antes de instalar la aplicación. |

Recuerde la información siguiente:

* Las visitas enviadas desde la aplicación pueden monitorearse mediante herramientas de monitoreado HTTP para verificar la atribución de adquisición.
* Para obtener más información acerca de cómo emitir `INSTALL_REFERRER`, consulte [Testing Google Play Campaign Measurement (Prueba de medición de campaña de Google Play)](https://developers.google.com/analytics/solutions/testing-play-campaigns) en la Guía para desarrolladores de Google.

* Se ha publicado una versión que corrige errores de adquisición en Android 4.8.2.

   Antes de realizar pruebas, actualice el SDK a la versión más reciente.

* Puede utilizar la herramienta Java `acquisitionTest.jar` que se proporciona para ayudarle a obtener el identificador exclusivo y el referente de instalación de emisión, lo que a su vez le ayuda a obtener la información en los pasos 3 al 12.

   **Instalación de la herramienta Java**

Para instalar la herramienta Java:

1. Descargue el archivo [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip).

1. Extraiga el archivo .jar.

   Puede ejecutar el archivo en la línea de comandos.

   Por ejemplo:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
