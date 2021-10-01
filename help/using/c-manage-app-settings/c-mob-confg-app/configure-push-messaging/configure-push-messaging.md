---
description: Puede usar esta información para configurar las opciones de los servicios push en la página Administrar configuración de aplicación a la hora de crear una aplicación nueva o editar una existente.
keywords: móvil
solution: Experience Cloud,Analytics
title: Configurar la mensajería push
topic-fix: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
exl-id: d4989c31-2692-4062-8fae-d41c3e3c179b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

# Configurar la mensajería push {#configure-push-messaging}

Puede usar esta información para configurar las opciones de los servicios push en la página Administrar configuración de aplicación a la hora de crear una aplicación nueva o editar una existente.

Antes de configurar la mensajería push, complete las tareas previas en [Requisitos previos para activar la mensajería push](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md).

* **Consideraciones sobre los grupos de informes**

   Puede configurar una aplicación de tienda de aplicaciones para Apple y otra para Google en cada grupo de informes. Si necesita aplicaciones adicionales, por ejemplo, una para un entorno de producción y otra para un entorno de desarrollo, configure una nueva aplicación de tienda de aplicaciones y un nuevo grupo de informes para cada entorno.

>[!IMPORTANT]
>
>No es posible migrar la aplicación a un nuevo grupo de informes. En caso de hacerlo, podría desajustarse la configuración de push y los mensajes no se enviarían.

1. En **[!UICONTROL Servicios push]**, rellene los siguientes campos:

   * Apple

      **[!UICONTROL Clave privada]**

      Busque y seleccione su clave privada válida: `.p12`, `.key` o `.pen`.

      >[!IMPORTANT]
      >Si el archivo que seleccione para la entrada **[!UICONTROL Clave privada]** contiene también un certificado, no es necesario especificar este.

   * **[!UICONTROL Certificado]**

      Especifique un certificado válido. Esta opción solo es necesaria si la entrada de **[!UICONTROL Clave privada]** **no** contiene ningún certificado. Para obtener más información sobre la obtención del certificado SSL y de la clave privada, consulte [Configuración de la aplicación para utilizar APNS o FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL Clave de API]**

      Especifique una clave de API válida. Para obtener más información sobre la obtención de la clave de API, consulte [Configuración de la aplicación para utilizar APNS o FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Para obtener más información, consulte los temas siguientes:

      * [Mensajería push en Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Mensajería push en iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Haga clic en **[!UICONTROL Guardar]**.
