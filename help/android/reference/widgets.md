---
description: Se puede realizar un seguimiento de los widgets de Android usando los mismos métodos que con la aplicación. Los widgets comparten el contexto de aplicación con su aplicación, por lo que se conservan el orden de visitas y la identificación de los visitantes.
keywords: android, biblioteca, mobile, móvil, sdk
seo-description: Se puede realizar un seguimiento de los widgets de Android usando los mismos métodos que con la aplicación. Los widgets comparten el contexto de aplicación con su aplicación, por lo que se conservan el orden de visitas y la identificación de los visitantes.
seo-title: Widgets de Android
solution: Experience Cloud,Analytics
title: Widgets de Android
topic: Desarrollador e implementación
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Widgets de Android {#android-widgets}

Se puede realizar un seguimiento de los widgets de Android usando los mismos métodos que con la aplicación. Los widgets comparten el contexto de aplicación con su aplicación, por lo que se conservan el orden de visitas y la identificación de los visitantes.

Las siguientes directrices le ayudarán a rastrear widgets de Android:

* No implemente llamadas a las métricas del ciclo vital (`stopActivity`/`startActivity`) en el widget.

* Para realizar un seguimiento de cuándo se agrega un widget a la pantalla de inicio, agregue una llamada `trackState` o `trackEvent` al método `onEnabled` del widget.

* Para realizar un seguimiento de cuándo se inicia la aplicación desde un widget, agregue una llamada `trackState` o `trackEvent` antes de crear un objeto Intent para iniciar la aplicación.

* Para realizar el seguimiento del contexto de una acción, puede definir una variable `ContextData` que proporcione la opción de segmentar cada acción separadamente (por ejemplo, `AppExperienceType="widget"` o `app`).

