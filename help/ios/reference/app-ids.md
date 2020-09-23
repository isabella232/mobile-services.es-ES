---
description: En la tabla siguiente se describen los distintos identificadores de aplicación que utilizan el SDK para iOS y Adobe Mobile Services.
seo-description: En la tabla siguiente se describen los distintos identificadores de aplicación que utilizan el SDK para iOS y Adobe Mobile Services.
seo-title: ID de la aplicación
solution: Experience Cloud,Analytics
title: ID de la aplicación
topic: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 61%

---


# ID de la aplicación {#app-ids}

En la tabla siguiente se describen los distintos identificadores de aplicación que utilizan el SDK para iOS y Adobe Mobile Services.

| ID | Descripción |
|--- |--- |
| ID enviado con métricas del ciclo vital | Es una combinación del nombre de la aplicación y la versión del paquete enviado a la tienda de aplicaciones.  Este valor se utiliza para el informe Versiones de Adobe Mobile Services. Puede utilizarlo para filtrar los resultados por versiones específicas de la aplicación. |
| ID de App Store | El almacén de aplicaciones asigna este ID a la aplicación y se proporciona en Adobe Mobile Services al crear vínculos de adquisición. |
| AppID en la configuración JSON de ADBMobile | Este es un ID exclusivo que Adobe Mobile Services asigna a la instancia de la aplicación para todos los metadatos asociados en el sistema.  Este ID se utiliza para crear las URL exclusivas para el seguimiento de adquisiciones o el vínculo de seguimientos, se agrega automáticamente al archivo de configuración JSON de ADBMobile cuando se descarga desde la interfaz de usuario y se puede encontrar en Administrar configuración de aplicación, dentro de los ajustes de Adquisición de la aplicación. |

