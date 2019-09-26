---
description: El seguimiento de adquisición debe estar activado en la configuración del SDK para poder realizar el seguimiento de los vínculos de marketing e informar al respecto.
keywords: móvil
seo-description: Acquisition tracking must be enabled in the SDK configuration before you can track and report on Marketing Links.
seo-title: Configurar la adquisición
solution: Marketing Cloud,Analytics
title: Configurar la adquisición
topic: Métricas
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Configurar la adquisición {#configure-acquisition}

El seguimiento de adquisición debe estar activado en la configuración del SDK para poder realizar el seguimiento de los vínculos de marketing e informar al respecto.

1. En la página Administrar configuración de aplicación de la aplicación, desplácese hasta la sección **[!UICONTROL Opciones de adquisición de SDK.]**
1. Complete las siguientes tareas:

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * Introduzca un valor en el campo Tiempo de espera de **[!UICONTROL referente (segundos)]**

      (**Opcional**) Si ha activado la casilla de verificación **[!UICONTROL Habilitar]** , este campo es opcional. Puede cambiar el valor de tiempo de espera, que se indica en segundos. This setting specifies the period to wait for Acquisition information before sending the First Launch hit.
   >[!IMPORTANT]
   >Debe especificar un valor distinto de cero. Si activa Adquisición pero deja el valor como cero, los vínculos de Adquisición no funcionarán. We recommend that you use the 5-second default value.

1. Descargue y use el nuevo archivo de configuración del SDK en su aplicación.

   Ha configurado correctamente la adquisición en **iOS**.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
