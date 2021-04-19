---
description: Puede configurar las opciones de SDK Analytics en la página Administrar configuración de aplicación a la hora de crear una aplicación nueva o editar una existente.
keywords: móvil
seo-description: Puede configurar las opciones de SDK Analytics en la página Administrar configuración de aplicación a la hora de crear una aplicación nueva o editar una existente.
seo-title: Configurar las opciones de SDK Analytics
solution: Experience Cloud,Analytics
title: Configurar las opciones de SDK Analytics
topic-fix: Metrics
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
exl-id: f2c35b65-1052-4bfc-af9d-8778e4ff0522
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 100%

---

# Configurar las opciones de SDK Analytics {#configure-sdk-analytics-options}

Puede configurar las opciones de SDK Analytics en la página Administrar configuración de aplicación a la hora de crear una aplicación nueva o editar una existente.

Rellene los campos siguientes en la sección **[!UICONTROL Opciones de SDK Analytics]**:

* **[!UICONTROL Utilizar HTTPS]**

   Active HTTPS para una mayor seguridad.

* **[!UICONTROL Antedatar coincidencias de sesión]**

   Activar o desactivar la capacidad de Adobe SDK de antedatar las coincidencias de información de la sesión. Actualmente, las coincidencias de información de sesión incluyen los bloqueos y la longitud de la sesión. Cuando se habilita, el SDK de Adobe antedatará la visita de información de sesión a 1 segundo después de la última visita individual de la sesión anterior. Esto significa que los datos de bloqueo y sesión se correlacionarán con la fecha exacta cuando se produjeron. Se antedatará una visita en cada uso nuevo de la aplicación. Al desactivarse, el SDK de Adobe adjuntará la información de la sesión al ciclo de vida actual.

* **[!UICONTROL Privacidad]**

   Seleccione una opción de privacidad

   * **[!UICONTROL Enviar datos hasta la exclusión]**
   * **[!UICONTROL Mantener datos hasta la inclusión]**

* **[!UICONTROL Tiempo de espera de sesión (en segundos)]**

   Especifique el valor de tiempo de espera de la sesión.

   El valor predeterminado es de 300 segundos. Especifica la duración en segundos que debe transcurrir entre el momento en que se inicia la aplicación, antes de que el inicio se considere una sesión nueva. Este tiempo de espera también se aplica cuando la aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación emplea en segundo plano no se incluye en la duración de la sesión.

* **[!UICONTROL Límite de lotes]**

   Especifique el número de coincidencias que desea poner en cola antes de enviar los datos.

   Si se establece en 0, las coincidencias se envían inmediatamente. El límite de lotes representa el umbral del número de visitas que se enviarán en llamadas consecutivas. Por ejemplo, si esta opción se establece en 10, las visitas anteriores a la décima se almacenarán en la cola. Cuando llega la décima, las 10 visitas se envían de forma consecutiva.

* **[!UICONTROL Más detalles]**

   Haga clic en el vínculo **[!UICONTROL Más detalles]** para ver el ID del grupo de informes y el servidor de seguimiento, activar o desactivar el seguimiento sin conexión y ver el modelo de codificación de caracteres utilizado (como UTF-8).

   Cuando el seguimiento sin conexión está habilitado, los datos generados por el dispositivo mientras está sin conexión se marcan con la hora y se envían más tarde. Si esta opción está desactivada, se descartan los datos sin conexión.
