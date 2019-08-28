---
description: Puede utilizar esta información para comprender mejor qué son los postbacks y cómo funcionan.
keywords: android; library; mobile; sdk
seo-description: Puede utilizar esta información para comprender mejor qué son los postbacks y cómo funcionan.
seo-title: Ejemplo de Postbacks
solution: Marketing Cloud, Analytics
title: Ejemplo de Postbacks
topic: Desarrollador e implementación
uuid: 8010 cd 00-d 42 b -4 e 16-8403-692 fab 2550 f 1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks example {#postbacks-example}

Puede utilizar esta información para ayudarle a comprender qué son los postbacks y cómo funcionan.

>[!CAUTION]
>
>Este ejemplo se proporciona únicamente con fines informativos. El archivo `ADBMobileConfig.json` debe configurarse en la interfaz de usuario de Adobe Mobile y no debería modificarse de forma manual. Un archivo de configuración editado de forma manual puede ser peligroso si tiene habilitada la configuración de mensajes remotos.

## `ADBMobileConfig.json` definición {#section_8751E8176F3546C09420341A39758AFF}

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

## Code sample {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. La URL reemplazará todas las variables de plantilla con los valores de la visita. Si la sesión anterior del usuario tuviera 132 segundos y ese usuario se encuentra en la versión 4.6.0 de Android SDK, la URL resultante tendrá este aspecto:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
