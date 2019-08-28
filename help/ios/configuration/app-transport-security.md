---
description: Esta información ayuda a trabajar con App Transport Security (ATS), que es un nuevo conjunto de requisitos de seguridad para iOS 9.
seo-description: Esta información ayuda a trabajar con App Transport Security (ATS), que es un nuevo conjunto de requisitos de seguridad para iOS 9.
seo-title: App Transport Security
solution: Marketing Cloud, Analytics
title: App Transport Security
topic: Desarrollador e implementación
uuid: e 9 ee 13 cf -9802-492 e -8 b 11-95 f 028 e 34 e 61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

Esta información ayuda a trabajar con App Transport Security (ATS), que es un nuevo conjunto de requisitos de seguridad para iOS 9.

A partir de iOS 9, Apple introdujo App Transport Security, un conjunto de requisitos que se ajusta a las prácticas recomendadas en conexiones seguras. Para obtener más información, consulte *nsapptransportsecurity* en [Referencia clave de lista de propiedades de información](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Para que el SDK de Adobe Mobile versión 4.7 o posterior funcione perfectamente con ATS, use la opción para habilitar SSL en la página Administrar configuración de aplicación. Para obtener más información, consulte [Administrar configuración de aplicación](/help/using/c-manage-app-settings/c-manage-app-settings.md) o [Configuración JSON de adbmobile](/help/ios/configuration/json-config/json-config.md).

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

Como alternativa, puede agregar servicios a los servidores siguientes:

| Producto | Instrucciones |
|--- |--- |
| Analytics | Para incluir el servidor de Analytics, agregue el dominio del servidor de seguimiento a su archivo info.plist como un dominio de excepción para ATS.  El dominio del servidor de seguimiento se puede encontrar en la sección Analytics del archivo `ADBMobileConfig.json` o en la sección Analytics de la página Administrar configuración de aplicación. |
| Audience Manager | El dominio de Audience Manager se encuentra en la propiedad server del objeto audienceManager, en el archivo `ADBMobileConfig.json`.  Si utiliza Audience Manager en su aplicación y SSL no está habilitado, agregue este servidor como un dominio de excepción para ATS en el archivo `Info.plist`. |
| Target | Puede agregar su punto final de Target al archivo Info.plist como un dominio de excepción para ATS.  Para encontrar el punto final de Target, busque `clientCodeproperty` en el objeto target del archivo `ADBMobileConfig.json`. Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Servicio de identidad de Adobe Experience Platform | Puede añadir el servidor de Experience Cloud como un dominio de excepción para ATS en el archivo `Info.plist`. This domain is `dpm.demdex.net`. |
| Mobile Services: adquisición | Incluya el servidor de adquisición como dominio de excepción para ATS en su archivo `Info.plist`. This domain is `c00.adobe.com`. |
| Mobile Services: mensajes en la aplicación | Si está utilizando mensajes en la aplicación, tal vez necesite agregar entradas en el dominio de excepción para ATS por cada URL que utilice que no sea HTTPS. Esta lista incluye las imágenes alojadas y cualquier URL incrustada en su mensaje HTML personalizado en pantalla completa.  Para obtener más información sobre la configuración del dominio de excepciones en un `info.plist` archivo, consulte la fila *nsexceptiondomains* en *la Tabla 2: Claves principales del diccionario de App Transport Security*. Consulte *también las claves de diccionario de dominios de excepciones de la tabla 3* en [Referencia clave de lista de propiedades de información](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Estas consideraciones afectan a las conexiones realizadas por el SDK de Adobe Mobile y no afectan a la vista web ni a otras conexiones realizadas por su aplicación.

