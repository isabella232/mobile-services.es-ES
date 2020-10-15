---
description: Definición y ejemplos de código fuente de la función Postback.
seo-description: Definición y ejemplos de código fuente de la función Postback.
seo-title: Ejemplo de Postback
solution: Experience Cloud,Analytics
title: Ejemplo de Postback
topic: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '124'
ht-degree: 100%

---


# Ejemplo de Postbacks {#postback-example}

Definición y ejemplos de código fuente de la función Postback.

>[!CAUTION]
>
>Este ejemplo tiene propósitos meramente informativos. El archivo `ADBMobileConfig.json` debe configurarse en la interfaz de usuario de Adobe Mobile y no debería modificarse de forma manual. Un archivo de configuración editado de forma manual puede ser peligroso si tiene habilitada la configuración de mensajes remotos.

## Definición de ADBMobileConfig.json {#section_0F6EC001AB6D488E815F50C7F5DA022E}

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

## Ejemplo de código {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Como su estado es `“MainMenu”`, esta llamada de seguimiento activa el mensaje de postback anterior. La URL reemplazará todas las variables de plantilla con los valores de la visita. Suponiendo que la sesión anterior del usuario tuviera una duración de 132 segundos y que el usuario utilice la versión 4.6.0 del SDK para iOS, la URL resultante tendría este aspecto:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
