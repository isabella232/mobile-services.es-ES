---
description: Puede utilizar esta información para comprender mejor qué son los postbacks y cómo funcionan.
keywords: android;library;mobile;sdk
seo-description: Puede utilizar esta información para comprender mejor qué son los postbacks y cómo funcionan.
seo-title: Ejemplo de Postbacks
solution: Experience Cloud,Analytics
title: Ejemplo de Postbacks
topic: Developer and implementation
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 100%

---


# Ejemplo de Postbacks {#postbacks-example}

Puede utilizar esta información para comprender mejor qué son los postbacks y cómo funcionan.

>[!CAUTION]
>
>Este ejemplo tiene propósitos meramente informativos. El archivo `ADBMobileConfig.json` debe configurarse en la interfaz de usuario de Adobe Mobile y no debería modificarse de forma manual. Un archivo de configuración editado de forma manual puede ser peligroso si tiene habilitada la configuración de mensajes remotos.

## Definición de `ADBMobileConfig.json` {#section_8751E8176F3546C09420341A39758AFF}

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

## Ejemplo de código {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Como su estado es `“MainMenu”`, esta llamada de seguimiento activa el mensaje de postback anterior. La URL reemplazará todas las variables de plantilla con los valores de la visita. Suponiendo que la sesión anterior del usuario tuviera una duración de 132 segundos y que el usuario utilice la versión 4.6.0 del SDK para Android, la URL resultante tendría este aspecto:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
