---
description: 'En la página Administrar configuración de aplicación, puede realizar los siguientes tipos de cambios '
title: Configurar su aplicación
uuid: c088e12d-73b6-40c4-b8cc-ec3bb3d3aa4a
exl-id: 52fd58ad-87b8-499b-9c46-c3176bcda37c
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 31%

---

# Configurar su aplicación {#configuring-your-app}

En la página Administrar configuración de aplicación, puede realizar los siguientes tipos de cambios:

* **Información de la aplicación**

   Esta sección incluye información como el nombre de la aplicación, el tipo, las métricas clave, el ciclo de vida y los informes de ubicación.

   * **Informes de ciclo de vida**

      >[!TIP]
      >
      >Si ha creado el grupo de informes en Adobe Analytics, debe activar los informes de ciclo de vida. Si ha creado el grupo de informes en Adobe Mobile, esta opción está habilitada de forma predeterminada.

      Este informe permite medir las siguientes métricas:

      * **Adquisición**

         Rastree las direcciones URL de referencia para las campañas de descarga de la aplicación. Para obtener más información, consulte [Adquisición](/help/using/acquisition-main/acquisition-main.md).

      * **Ciclo de vida**

         Rastree las métricas y dimensiones que la biblioteca móvil puede medir automáticamente una vez implementado el ciclo vital. Para obtener más información, consulte las secciones siguientes:

         * [Métricas del ciclo vital del SDK de iOS](/help/ios/metrics.md)
         * [Métricas del ciclo vital de Android](/help/android/metrics.md)
         * [Métricas del ciclo vital de Windows](/help/universal-windows/metrics.md)
         * [Métricas del ciclo vital de BlackBerry](/help/blackberry/metrics.md)
      * **Acciones de la aplicación**

         Habilite informes y rutas basadas en acciones internas de la aplicación.

      * **Valor de duración**

         Comprenda cómo acumulan valor los usuarios a lo largo del tiempo mediante los KPI de la aplicación, como compras, vistas de anuncios, vídeos completos, compartido en medios sociales, cargas de fotografías, etc.

      * **Eventos temporizados**

         Mida la cantidad de tiempo que transcurre (en la aplicación y el tiempo total) entre las acciones clave de la aplicación (como el tiempo transcurrido hasta la primera compra).


* **Informes de ubicación**

   Esta opción permite activar informes para realizar un seguimiento de la latitud y la longitud, así como identificar puntos de interés (POI) específicos. También puede realizar el seguimiento de señalizaciones Bluetooth (UUID, principal, secundaria y proximidad).

* **SDK de aplicación y herramientas para el desarrollador y el evaluador**

   >[!IMPORTANT]
   >
   >Antes de descargar los SDK y las herramientas, debe configurar las opciones de SDK Analytics. Para obtener más información, consulte [Configuración de las opciones de SDK Analytics](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md).

   Cuando esté listo para actualizar a los SDK 4.x, o si está trabajando en una aplicación nueva, descargue los SDK y las herramientas de desarrollo más recientes desde la parte inferior de la página Administrar configuración de aplicación.

   Una vez completada la configuración, puede enviar el archivo de configuración a los desarrolladores para que los datos se puedan recopilar correctamente. Si no está listo para descargarlos ahora, haga clic en Administrar configuración de aplicación y luego en la aplicación para mostrar la página Información de la aplicación en cualquier momento.
