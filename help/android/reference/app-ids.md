---
description: En la tabla siguiente se describen los distintos identificadores de aplicación que utilizan el SDK para Android y Adobe Mobile Services.
seo-description: En la tabla siguiente se describen los distintos identificadores de aplicación que utilizan el SDK para Android y Adobe Mobile Services.
seo-title: ID de la aplicación
solution: Experience Cloud,Analytics
title: ID de la aplicación
topic-fix: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
exl-id: 28358dd6-50dd-4ba9-9fb0-5271eae69d28
source-git-commit: bb2459e57274183e55c1facd1a510cf55a83ddb4
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 100%

---

# ID de la aplicación {#app-ids}

En la tabla siguiente se describen los distintos identificadores de aplicación que utilizan el SDK para Android y Adobe Mobile Services.

| ID | Descripción |
|--- |--- |
| ID enviado con métricas del ciclo vital | Es una combinación del nombre de la aplicación y la versión del paquete enviado a la tienda de aplicaciones. Este valor se utiliza para el informe Versiones de Adobe Mobile Services. Puede utilizarlo como filtro para segmentar por versiones específicas de la aplicación. |
| ID de App Store | Este ID se lo asigna a la aplicación la tienda de aplicaciones y se proporciona en Adobe Mobile Services cuando crea vínculos de adquisición. |
| AppID en la configuración JSON de ADBMobile | Es un ID único que Adobe Mobile Services asigna a la instancia de la aplicación para todos los metadatos asociados en el sistema. Este ID se utiliza para crear las direcciones URL exclusivas para el seguimiento de adquisiciones o el vínculo de seguimientos. Este identificador se añade automáticamente al archivo de configuración JSON de ADBMobile cuando el archivo se descarga desde la interfaz de usuario y se puede encontrar en Administrar configuración de la aplicación, en los ajustes de Adquisición de la aplicación. |
