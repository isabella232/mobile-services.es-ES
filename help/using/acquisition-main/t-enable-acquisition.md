---
description: El seguimiento de la adquisición debe estar habilitado en la configuración del SDK para poder rastrear e informar sobre vínculos de marketing.
keywords: móvil
seo-description: El seguimiento de la adquisición debe estar habilitado en la configuración del SDK para poder rastrear e informar sobre vínculos de marketing.
seo-title: Configurar la adquisición
solution: Marketing Cloud, Analytics
title: Configurar la adquisición
topic: Métricas
uuid: e 996 e 43 e -8 a 77-47 a 3-a 6 fb -53 f 676 f 92 bef
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Configurar la adquisición {#configure-acquisition}

El seguimiento de la adquisición debe estar habilitado en la configuración del SDK para poder rastrear e informar sobre vínculos de marketing.

1. En la página Administrar configuración de aplicación de la aplicación, desplácese hasta la sección **[!UICONTROL Opciones de adquisición de SDK.]**
1. Complete las siguientes tareas:

   * To enable Acquisition, select the **[!UICONTROL Enable]** check box.

      When you select this check box, the **[!UICONTROL Referrer Timeout]** field becomes active, and the value changes from 0 to 5.

   * Ingrese un valor en el campo Tiempo de espera **[!UICONTROL de referente (en segundos)]**

      (**Opcional**) Si habilitó **[!UICONTROL la]** casilla Activar, este campo es opcional. Puede cambiar el valor de tiempo de espera, que se indica en segundos. Esta configuración especifica el período para esperar la información de adquisición antes de enviar la visita del primer lanzamiento.
   >[!IMPORTANT]
   >Debe especificar un valor distinto de cero. Si activa la adquisición pero deja el valor como cero, los vínculos de adquisición no funcionarán. Le recomendamos que utilice el valor predeterminado de 5 segundos.

1. Descargue y use el nuevo archivo de configuración del SDK en su aplicación.

   Ha configurado correctamente la adquisición en **iOS**.
To enable Acquisition on **Android**, complete the steps in [Tracking Mobile Acquisition](/help/android/acquisition-main/acquisition.md).
