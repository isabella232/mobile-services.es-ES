---
description: Esta información ayuda a trabajar con App Transport Security (ATS), que es un nuevo conjunto de requisitos de seguridad para iOS 9.
seo-description: Esta información ayuda a trabajar con App Transport Security (ATS), que es un nuevo conjunto de requisitos de seguridad para iOS 9.
seo-title: App Transport Security
solution: Experience Cloud,Analytics
title: App Transport Security
topic: Desarrollador e implementación
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

Esta información ayuda a trabajar con App Transport Security (ATS), que es un nuevo conjunto de requisitos de seguridad para iOS 9.

A partir de iOS 9, Apple introdujo App Transport Security, un conjunto de requisitos que se ajusta a las prácticas recomendadas en conexiones seguras. Para obtener más información, consulte *NSAppTransportSecurity* en [Clave de lista de propiedades de información](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Para que el SDK de Adobe Mobile versión 4.7 o posterior funcione perfectamente con ATS, use la opción para habilitar SSL en la página Administrar configuración de aplicación. Para obtener más información, consulte [Administrar configuración de la aplicación](/help/using/c-manage-app-settings/c-manage-app-settings.md) o [Configuración JSON de ADBMobile](/help/ios/configuration/json-config/json-config.md).

En Adobe Mobile Services, al seleccionar la opción **[!UICONTROL Utilizar HTTPS]** en la página Administrar configuración de aplicación, todas las visitas de Analytics, Audience Manager, Target y los servicios de ID de Adobe Experience Platform se envían mediante HTTPS.

Como alternativa, puede elegir incluir el servicio para los servidores siguientes:

| Producto | Instrucciones |
|--- |--- |
| Analytics | Para incluir el servidor de Analytics, agregue el dominio del servidor de seguimiento a su archivo info.plist como un dominio de excepción para ATS.  El dominio del servidor de seguimiento se puede encontrar en la sección Analytics del archivo `ADBMobileConfig.json` o en la sección Analytics de la página Administrar configuración de aplicación. |
| Audience Manager | El dominio de Audience Manager se encuentra en la propiedad server del objeto audienceManager, en el archivo `ADBMobileConfig.json`. Si utiliza Audience Manager en su aplicación y SSL no está habilitado, agregue este servidor como un dominio de excepción para ATS en el archivo `Info.plist`. |
| Target | Puede agregar su punto final de Target al archivo Info.plist como un dominio de excepción para ATS.  Para encontrar el punto final de Target, busque `clientCodeproperty` en el objeto target del archivo `ADBMobileConfig.json`. El punto final será `https://{clientCode}.tt.omtrdc.net`.  Por ejemplo, si su `clientCodeproperty` es `“myCompany”`, el punto final será `https://myCompany.tt.omtrdc.net`. |
| Servicio de ID de Adobe Experience Platform | Puede añadir el servidor de Experience Cloud como un dominio de excepción para ATS en el archivo `Info.plist`. Este dominio es `dpm.demdex.net`. |
| Mobile Services: adquisición | Incluya el servidor de adquisición como dominio de excepción para ATS en su archivo `Info.plist`. Este dominio es `c00.adobe.com`. |
| Mobile Services: mensajes en la aplicación | Si está utilizando mensajes en la aplicación, tal vez necesite agregar entradas en el dominio de excepción para ATS por cada URL que utilice que no sea HTTPS. Esta lista incluye las imágenes alojadas y cualquier URL incrustada en su mensaje HTML personalizado en pantalla completa.  Para obtener más información sobre la configuración del dominio de excepciones en un archivo `info.plist`, consulte la fila *NSExceptionDomains* en la *Tabla 2: Claves principales del diccionario de seguridad de transporte de aplicaciones*. Consulte también la *Tabla 3 Claves de diccionario de dominios de excepción* en la [Clave de lista de propiedades de información](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Estas consideraciones afectan a las conexiones que realiza el SDK móvil de Adobe y no tienen impacto en las visualizaciones web ni en otras conexiones realizadas por la aplicación.

