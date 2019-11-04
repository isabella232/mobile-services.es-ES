---
description: Un grupo de informes virtuales (VRS) se crea aplicando una o varias definiciones de segmentos a un grupo de informes. Esto permite a los usuarios mantener sus datos en un grupo de informes y gestionarlos como si estuvieran en grupos distintos.
seo-description: Un grupo de informes virtuales (VRS) se crea aplicando una o varias definiciones de segmentos a un grupo de informes. Esto permite a los usuarios mantener sus datos en un grupo de informes y gestionarlos como si estuvieran en grupos distintos.
seo-title: Grupos de informes virtuales
title: Grupos de informes virtuales
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: ht
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Grupos de informes virtuales {#virtual-report-suites}

Un grupo de informes virtuales (VRS) se crea aplicando una o varias definiciones de segmentos a un grupo de informes. Esto permite a los usuarios mantener sus datos en un grupo de informes y gestionarlos como si estuvieran en grupos distintos.

Las aplicaciones que usan VRS hacen lo mismo que las aplicaciones que usan grupos de informes corrientes, excepto en la administración de las siguientes funciones:

* Reglas de procesamiento
* eVars/props/variables de lista/eventos
* Opción habilitada para marca de hora
* Marcas de dimensión (ciclo de vida, ubicación, etc.)
* Clasificaciones

Estos valores se administran en el grupo de informes principal y se comparten con los VRS que pertenecen a él.

Puede acceder a las áreas siguientes desde la interfaz de usuario de Adobe Mobile Services independientemente del grupo de informes principal:

* El archivo de configuración
* Administrar puntos de interés
* Administrar destinos de vínculo
* Administrar postbacks
* Administrar vínculos
* Adquisición

Un VRS sirve para completar las tareas siguientes:

* Restringir el acceso a los datos:

   Una empresa multinacional tiene una aplicación que envía datos a un grupo de informes para todas las ubicaciones geográficas. Sin embargo, la empresa quiere restringir el acceso de un usuario del negocio de una región para impedir que vea los datos de otra región. El administrador de la empresa puede crear un VRS para segmentar a los usuarios por región y dar permiso para acceder a este VRS solo al usuario del negocio que administra la región.

   Esta restricción impide que los usuarios del negocio vean datos que no están relacionados con su región. Por ejemplo, un usuario del negocio de EMEA no necesita conocer los datos de la región APAC.

* Permitir el control de la mensajería en la aplicación/push, los puntos de interés de ubicación, la adquisición y los postbacks, y hacer que todos los datos se envíen a un grupo de informes:

   Una empresa multinacional quiere que todos los datos se envíen al mismo grupo de informes para todas las ubicaciones geográficas. No obstante, la empresa quiere que el equipo de marketing de cada región gestione su propia mensajería en la aplicación/push. El administrador de la empresa puede crear VRS regionales y cada equipo puede gestionar su propia aplicación en función de ese VRS.

   El equipo regional crea su aplicación usando el archivo de configuración del VRS. Los datos se envían al grupo de informes principal, pero la mensajería en la aplicación/push, los puntos de interés de ubicación, las adquisiciones y los postbacks se controlan en la aplicación que se creó desde el VRS.

## Crear un grupo de informes virtuales en Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Solo los administradores de Adobe Analytics pueden crear y modificar grupos de informes virtuales en Adobe Analytics. Para crear un grupo de informes virtuales, consulte [Creación de grupos de informes virtuales](https://docs.adobe.com/content/help/es-ES/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

Cada VRS tiene un identificador único. Para ver el ID del grupo de informes principal en la interfaz de usuario de Adobe Mobile Services, en la página Administrar configuración de aplicación, en la sección **[!UICONTROL Información de la aplicación]**, haga clic en **[!UICONTROL Más detalles]**.

En la interfaz de usuario de Adobe Mobile Services, puede usar un VRS para crear una aplicación y segmentar los datos para un grupo determinado de la organización. De esta forma, por ejemplo, un usuario del negocio de España no puede ver los datos que corresponden a un usuario del negocio ubicado en Japón.

>[!TIP]
>
>Los valores que se heredan del grupo de informes principal no se pueden modificar.

Un VRS es una definición de segmento del lado del servidor que se adjunta a un grupo de informes principal. Como resultado, no se puede llevar a cabo una recopilación de datos para los VRS ya que el SDK solo envía las visitas al grupo de informes principal, que, a su vez, las registra.

## Grupo de informes virtuales en Adobe Mobile Services y recopilación de datos {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

En Adobe Mobile Services, puede crear una aplicación basada en un grupo de informes principal o virtual. Al crear una aplicación basada en un grupo de informes virtuales, le recomendamos que alinee el segmento del VRS con la definición de la aplicación.

>[!TIP]
>
>Las certificaciones push se adjuntan en el nivel de la aplicación en la interfaz de usuario de Mobile Services.

Para asegurarse de que los mensajes push se envían correctamente, el segmento de audiencia se tiene que definir correctamente. Para obtener más información, consulte [Audiencia: definir y configurar segmentos de audiencia para los mensajes push](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Sobre las zonas horarias {#section_498E1EED22D741C3BDED44F01FACA72A}

La propiedad de zona horaria de la página Administrar configuración de aplicación es diferente de la propiedad de zona horaria que se usa para crear el VRS en Adobe Analytics. La propiedad que hay en la página Administrar configuración de aplicación se hereda del grupo de informes principal, que se emplea para enviar datos a Adobe Analytics. La propiedad que especifica al crear el VRS en Adobe Analytics se utiliza para mostrar los informes en la interfaz de usuario de Mobile Services y podría diferir de la que hay en el grupo de informes principal.

## Seleccionar un grupo de informes virtuales en la interfaz de usuario de Mobile Services {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Para usar un VRS cuando cree una aplicación, selecciónelo en la lista desplegable **[!UICONTROL Grupo de informes]** de la página Información de la aplicación. Esta lista contiene grupos de informes principales y virtuales.

>[!IMPORTANT]
>
>Para seleccionar un VRS de la lista, busque una opción con el punto azul y el formato de nombre `vrs_` *`<company_name>`* `_` *`<unique name>`*.

## Propiedades de los grupos de informes virtuales {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Estas son las propiedades de los VRS:

>[!TIP]
>
>Las propiedades de solo lectura se heredan del grupo de informes principal.

| Propiedad | Heredada del grupo de informes principal | ¿Editable? | Notas |
|--- |--- |--- |--- |
| `target.clientCode` | No | Sí |  |
| `target.timeout` | No | Sí |  |
| `audienceManager.server` | No | Sí |  |
| `audienceManager.analyticsForwardingEnabled` | Sí | Sí |  |
| `audienceManager.timeout` | No | Sí |  |
| `acquisition.server` | No | No |  |
| `acquisition.appid` | No | No |  |
| `analytics.rsids` | Sí | No |  |
| `analytics.server` | No | No |  |
| `analytics.ssl` | No | Sí |  |
| `analytics.offlineEnabled` | Sí |  |  |
| `analytics.charset` | Sí | No |  |
| `analytics.lifecycleTimeout` | No | Sí | Debe ser el grupo de informes principal para que exista coherencia entre los datos. |
| `analytics.privacyDefault` | No | Sí |  |
| `analytics.batchLimit` | No | Sí |  |
| `analytics.timezone` | Sí | Sí, al crear la aplicación. | Esta propiedad de zona horaria se usa para enviar datos a Adobe Analytics y es diferente de la propiedad de zona horaria que se establece cuando se crea un VRS. |
| `analytics.timezoneOffset` | Sí | No |  |
| `analytics.referrerTimeout` | No | Sí |  |
| `analytics.backdateSessionInfo` | Sí | Sí |  |

## Información adicional {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

A continuación se proporciona información adicional sobre los grupos de informes virtuales:

* Para obtener más información sobre los VRS, consulte [Grupos de informes virtuales](https://docs.adobe.com/content/help/es-ES/analytics/components/virtual-report-suites/vrs-about.html).
* Para obtener más información sobre cómo planificar la implementación de un VRS, consulte [Flujo de trabajo del grupo de informes virtuales](https://docs.adobe.com/content/help/es-ES/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).