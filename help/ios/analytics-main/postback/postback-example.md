---
description: Definición y ejemplos de código fuente de la función Postback.
seo-description: Definición y ejemplos de código fuente de la función Postback.
seo-title: Ejemplo de Postback
solution: Marketing Cloud, Analytics
title: Ejemplo de Postback
topic: Desarrollador e implementación
uuid: 809 c 5646-7 a 80-40 df -984 b -0 af 89 d 854259
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postback example {#postback-example}

Definición y ejemplos de código fuente de la función Postback.

>[!CAUTION]
>
>Este ejemplo se proporciona únicamente con fines informativos. El archivo `ADBMobileConfig.json` debe configurarse en la interfaz de usuario de Adobe Mobile y no debería modificarse de forma manual. Un archivo de configuración editado de forma manual puede ser peligroso si tiene habilitada la configuración de mensajes remotos.

## ADBMobileConfig.json definition {#section_0F6EC001AB6D488E815F50C7F5DA022E}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## Code sample {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. La dirección URL sustituye todas las variables de plantilla por valores de la visita. Si la sesión anterior del usuario tuviera 132 segundos y ese usuario se encuentra en la versión 4.6.0 de iOS SDK, aquí se muestra un ejemplo de la URL resultante:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`