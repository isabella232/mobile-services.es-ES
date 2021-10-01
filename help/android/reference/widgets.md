---
description: Los widgets de Android se pueden rastrear utilizando los mismos métodos que se emplean en la aplicación. Los widgets comparten el contexto de la aplicación con la aplicación, por lo que se conservan el orden de visitas y la identificación del visitante.
keywords: android, biblioteca, mobile, móvil, sdk
solution: Experience Cloud,Analytics
title: Widgets de Android
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%

---

# Widgets de Android {#android-widgets}

Los widgets de Android se pueden rastrear utilizando los mismos métodos que se emplean en la aplicación. Los widgets comparten el contexto de la aplicación con la aplicación, por lo que se conservan el orden de visitas y la identificación del visitante.

Las siguientes directrices le ayudarán a hacer el seguimiento de las utilidades de Android:

* No implemente llamadas a las métricas del ciclo vital (`stopActivity`/`startActivity`) en el widget.

* Para realizar un seguimiento de cuándo se agrega un widget a la pantalla de inicio, agregue una llamada `trackState` o `trackEvent` al método `onEnabled` del widget.

* Para realizar un seguimiento de cuándo se inicia la aplicación desde un widget, agregue una llamada `trackState` o `trackEvent` antes de crear un objeto Intent para iniciar la aplicación.

* Para realizar el seguimiento del contexto de una acción, puede definir una variable `ContextData` que proporcione la opción de segmentar cada acción separadamente (por ejemplo, `AppExperienceType="widget"` o `app`).
