---
description: En la tabla siguiente se describen los distintos identificadores de aplicación que utilizan el SDK para iOS y Adobe Mobile Services.
solution: Experience Cloud,Analytics
title: ID de la aplicación
topic-fix: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
exl-id: 82f0a097-b2eb-4313-8624-dd442e3da039
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 100%

---

# ID de la aplicación {#app-ids}

En la tabla siguiente se describen los distintos identificadores de aplicación que utilizan el SDK para iOS y Adobe Mobile Services.

| ID | Descripción |
|--- |--- |
| ID enviado con métricas del ciclo vital | Es una combinación del nombre de la aplicación y la versión del paquete enviado a la tienda de aplicaciones.  Este valor se utiliza para el informe Versiones de Adobe Mobile Services. Puede utilizarlo para filtrar los resultados por versiones específicas de la aplicación. |
| ID de App Store | La tienda de aplicaciones asigna este ID a la aplicación y se proporciona en Adobe Mobile Services cuando crea vínculos de adquisición. |
| AppID en la configuración JSON de ADBMobile | Este es un ID único que Adobe Mobile Services asigna a la instancia de la aplicación para todos los metadatos asociados en el sistema.  Este ID se utiliza para crear las URL exclusivas para el seguimiento de adquisiciones o el vínculo de seguimientos, se agrega automáticamente al archivo de configuración JSON de ADBMobile cuando se descarga desde la interfaz de usuario y se puede encontrar en Administrar configuración de aplicación, dentro de los ajustes de Adquisición de la aplicación. |
