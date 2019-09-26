---
description: La siguiente tabla describe los distintos ID de aplicación que emplean el SDK para Android y Adobe Mobile Services.
seo-description: La siguiente tabla describe los distintos ID de aplicación que emplean el SDK para Android y Adobe Mobile Services.
seo-title: ID de la aplicación
solution: Marketing Cloud,Analytics
title: ID de la aplicación
topic: Desarrollador e implementación
uuid: 3ac99489-6269-439e-a814-24102ef220b1
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# ID de la aplicación{#app-ids}

La siguiente tabla describe los distintos ID de aplicación que emplean el SDK para Android y Adobe Mobile Services.

| ID | Descripción |
|--- |--- |
| ID enviado con métricas del ciclo vital | Es una combinación del nombre de la aplicación y la versión del paquete enviado a la tienda de aplicaciones. Este valor se utiliza para el informe Versiones de Adobe Mobile Services. Puede utilizarlo como filtro para segmentar por versiones específicas de la aplicación. |
| ID de App Store | This ID is assigned to your app by the app store and is provided in Adobe Mobile services when you create acquisition links. |
| AppID en la configuración JSON de ADBMobile | Es un ID exclusivo que Adobe Mobile Services asigna a la instancia de la aplicación para todos los metadatos asociados en el sistema. Este ID se utiliza para crear las direcciones URL exclusivas para el seguimiento de adquisiciones o el vínculo de seguimientos. Este identificador se añade automáticamente al archivo de configuración JSON de ADBMobile cuando el archivo se descarga desde la interfaz de usuario y se puede encontrar en Administrar configuración de la aplicación, en los ajustes de Adquisición de la aplicación. |