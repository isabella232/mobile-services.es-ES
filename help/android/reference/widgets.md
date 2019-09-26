---
description: Se puede realizar un seguimiento de los widgets de Android usando los mismos métodos que con la aplicación. Los widgets comparten el contexto de aplicación con su aplicación, por lo que se conservan el orden de visitas y la identificación de los visitantes.
keywords: android;library;mobile;sdk
seo-description: Se puede realizar un seguimiento de los widgets de Android usando los mismos métodos que con la aplicación. Los widgets comparten el contexto de aplicación con su aplicación, por lo que se conservan el orden de visitas y la identificación de los visitantes.
seo-title: Android widgets
solution: Marketing Cloud,Analytics
title: Widgets de Android
topic: Desarrollador e implementación
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android widgets {#android-widgets}

Se puede realizar un seguimiento de los widgets de Android usando los mismos métodos que con la aplicación. Los widgets comparten el contexto de aplicación con su aplicación, por lo que se conservan el orden de visitas y la identificación de los visitantes.

Las siguientes directrices le ayudarán a rastrear widgets de Android:

* Do not implement lifecycle metrics ( `startActivity`/ `stopActivity`) calls in the widget.

* Para realizar un seguimiento de cuándo se agrega un widget a la pantalla de inicio, agregue una llamada `trackState` o `trackEvent` al método `onEnabled` del widget.

* Para realizar un seguimiento de cuándo se inicia la aplicación desde un widget, agregue una llamada `trackState` o `trackEvent` antes de crear un objeto Intent para iniciar la aplicación.

* To track the context of an action, you can define a `ContextData` variable that provides the option to segment each action separately (for example, `AppExperienceType="widget"` vs. `app`).

