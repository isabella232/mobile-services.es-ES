---
description: Puede configurar las opciones de SDK Analytics en la página Administrar configuración de aplicación a la hora de crear una aplicación nueva o editar una existente.
keywords: móvil
seo-description: Puede configurar las opciones de SDK Analytics en la página Administrar configuración de aplicación a la hora de crear una aplicación nueva o editar una existente.
seo-title: Configurar las opciones de SDK Analytics
solution: Experience Cloud,Analytics
title: Configurar las opciones de SDK Analytics
topic: Métricas
uuid: fd3a21d2-6560-4e96-92fe-b99caac5e834
translation-type: ht
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Configurar las opciones de SDK Analytics {#configure-sdk-analytics-options}

Puede configurar las opciones de SDK Analytics en la página Administrar configuración de aplicación a la hora de crear una aplicación nueva o editar una existente.

Rellene los campos siguientes en la sección **[!UICONTROL Opciones de SDK Analytics]**:

* **[!UICONTROL Utilizar HTTPS]**

   Active HTTPS para una mayor seguridad.

* **[!UICONTROL Antedatar coincidencias de sesión]**

   Activar o desactivar la capacidad de Adobe SDK de antedatar las coincidencias de información de la sesión. Actualmente, las coincidencias de información de sesión incluyen los bloqueos y la longitud de la sesión. Al activarse, Adobe SDK antedatará la coincidencia de información de la sesión un segundo después de la última coincidencia de la sesión anterior. Esto significa que los bloqueos y los datos de la sesión estarán correlacionados con la fecha correcta en la que tuvieron lugar. Se antedatará una visita en cada uso nuevo de la aplicación. Al desactivarse, el SDK de Adobe adjuntará la información de la sesión al ciclo de vida actual.

* **[!UICONTROL Privacidad]**

   Seleccione una opción de privacidad

   * **[!UICONTROL Enviar datos hasta la exclusión]**
   * **[!UICONTROL Mantener datos hasta la inclusión]**

* **[!UICONTROL Tiempo de espera de sesión (en segundos)]**

   Especifique el valor de tiempo de espera de la sesión.

   El valor predeterminado es de 300 segundos. Especifica la duración, en segundos, que debe transcurrir entre cada inicio de aplicación antes de que el inicio se considere como una nueva sesión. Este tiempo de espera también se aplica cuando su aplicación se envía al segundo plano y se reactiva. El tiempo que la aplicación permanece en segundo plano no se incluye en la duración de la sesión.

* **[!UICONTROL Límite de lotes]**

   Especifique el número de coincidencias que desea poner en cola antes de enviar los datos.

   Si se establece en 0, las coincidencias se envían inmediatamente. El límite de lotes representa el umbral del número de coincidencias que se pueden enviar en llamadas consecutivas. Por ejemplo, si esta opción se establece en 10, las coincidencias anteriores a la décima se almacenarán en la cola. Cuando llega la décima, las 10 coincidencias se envían de forma consecutiva.

* **[!UICONTROL Más detalles]**

   Haga clic en el vínculo **[!UICONTROL Más detalles]** para ver el ID del grupo de informes y el servidor de seguimiento, activar o desactivar el seguimiento sin conexión y ver el modelo de codificación de caracteres utilizado (como UTF-8).

   Al activar el seguimiento offline, se agrega una marca de hora a los datos que genera el dispositivo offline para enviarlos posteriormente. Si se desactiva esta opción, los datos offline se descartarán.
