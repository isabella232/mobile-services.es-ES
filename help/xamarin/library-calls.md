---
description: Información para ayudarle a realizar llamadas al complemento desde sus scripts.
keywords: Xamarin
solution: Experience Cloud Services
title: Realización de llamadas a la biblioteca
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# Realización de llamadas a la biblioteca{#making-calls-to-the-library}

Esta información le ayuda a realizar llamadas al complemento desde sus scripts.

Cuando desee realizar llamadas al complemento desde las secuencias de comandos, debe importar el área de nombres.

Usando `Com.Adobe.Mobile`:

* **iOS**: Después de importar el área de nombres, puede realizar llamadas directamente al SDK mediante los métodos estáticos del `ADBMobile` clases .

* **Android**: Puede realizar llamadas directamente al SDK mediante los métodos estáticos del `Config/Analytics/Target/AudienceManager/Media`clases .
