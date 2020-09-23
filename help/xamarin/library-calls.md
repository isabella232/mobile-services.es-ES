---
description: Información para ayudarle a realizar llamadas al complemento desde sus scripts.
keywords: Xamarin
seo-description: Información para ayudarle a realizar llamadas al complemento desde sus scripts.
seo-title: Realización de llamadas a la biblioteca
solution: Experience Cloud
title: Realización de llamadas a la biblioteca
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 13%

---


# Realización de llamadas a la biblioteca{#making-calls-to-the-library}

Esta información le ayudará a realizar llamadas al complemento desde sus scripts.

Cuando desee realizar llamadas al complemento desde sus scripts, debe importar la Área de nombres.

Mediante `Com.Adobe.Mobile`:

* **iOS**: Después de importar la Área de nombres, puede realizar llamadas directamente al SDK a través de los métodos estáticos de las `ADBMobile` clases.

* **Android**: Puede realizar llamadas directamente al SDK mediante los métodos estáticos de las `Config/Analytics/Target/AudienceManager/Media`clases.

