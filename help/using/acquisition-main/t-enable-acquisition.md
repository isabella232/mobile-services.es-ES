---
description: El seguimiento de adquisición debe estar activado en la configuración de SDK para que pueda realizar el seguimiento y elaborar informes sobre los vínculos de marketing.
keywords: móvil
solution: Experience Cloud,Analytics
title: Configurar la adquisición
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---

# Configurar la adquisición {#configure-acquisition}

El seguimiento de adquisición debe estar activado en la configuración de SDK para que pueda realizar el seguimiento y elaborar informes sobre los vínculos de marketing.

1. En la página Administrar configuración de aplicación de la aplicación, desplácese hasta la sección **[!UICONTROL Opciones de adquisición de SDK.]**
1. Complete las siguientes tareas:

   * Para activar la adquisición, marque la casilla de verificación **[!UICONTROL Habilitar]**.

      Al marcar esta casilla de verificación, el campo **[!UICONTROL Tiempo de espera de referente]** se activa y el valor cambia de 0 a 5 segundos.

   * Introduzca un valor en el campo **[!UICONTROL Tiempo de espera de referente (segundos)]**

      (**Opcional**) Si ha activado la casilla de verificación **[!UICONTROL Habilitar]**, este campo es opcional. Puede cambiar el valor de tiempo de espera, que se indica en segundos. Este valor especifica el tiempo de espera para la información de adquisición antes de enviar la visita del primer lanzamiento.
   >[!IMPORTANT]
   >Debe especificar un valor distinto de cero. Si activa la adquisición y deja el valor en cero, los vínculos de adquisición no funcionarán. Le recomendamos que utilice el valor predeterminado de 5 segundos.

1. Descargue y use el nuevo archivo de configuración del SDK en su aplicación.

   Ha configurado correctamente la adquisición en **iOS**. 
Para activar la adquisición en **Android**, realice los pasos que se detallan en [Seguimiento de adquisición móvil](/help/android/acquisition-main/acquisition.md).
