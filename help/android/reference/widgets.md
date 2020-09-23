---
description: Los widgets de Android se pueden rastrear utilizando los mismos métodos que la aplicación. Los widgets comparten el contexto de la aplicación con la aplicación, por lo que se conservan el orden de visitas y la identificación del visitante.
keywords: android;library;mobile;sdk
seo-description: Los widgets de Android se pueden rastrear utilizando los mismos métodos que la aplicación. Los widgets comparten el contexto de la aplicación con la aplicación, por lo que se conservan el orden de visitas y la identificación del visitante.
seo-title: Widgets de Android
solution: Experience Cloud,Analytics
title: Widgets de Android
topic: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 46%

---


# Widgets de Android {#android-widgets}

Los widgets de Android se pueden rastrear utilizando los mismos métodos que la aplicación. Los widgets comparten el contexto de la aplicación con la aplicación, por lo que se conservan el orden de visitas y la identificación del visitante.

Las siguientes directrices le ayudarán a realizar el seguimiento de las utilidades de Android:

* No implemente llamadas a las métricas del ciclo vital (`stopActivity`/`startActivity`) en el widget.

* Para realizar un seguimiento de cuándo se agrega un widget a la pantalla de inicio, agregue una llamada `trackState` o `trackEvent` al método `onEnabled` del widget.

* Para realizar un seguimiento de cuándo se inicia la aplicación desde un widget, agregue una llamada `trackState` o `trackEvent` antes de crear un objeto Intent para iniciar la aplicación.

* Para realizar el seguimiento del contexto de una acción, puede definir una variable `ContextData` que proporcione la opción de segmentar cada acción separadamente (por ejemplo, `AppExperienceType="widget"` o `app`).

