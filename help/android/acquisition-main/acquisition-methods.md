---
description: 'La biblioteca Android proporciona los siguientes métodos de adquisición '
keywords: android; library; mobile; sdk
seo-description: 'La biblioteca Android proporciona los siguientes métodos de adquisición '
seo-title: Métodos de adquisición
solution: Marketing Cloud, Analytics
title: Métodos de adquisición
topic: Desarrollador e implementación
uuid: 22 ec 432 f-e 7 ae -4 e 89-be 07-26-26206 bbeacf 8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

La biblioteca Android proporciona el método de adquisición siguiente:

* **campaignStartForApp**

   Permite a los desarrolladores iniciar una campaña de adquisición de aplicación como si el usuario hubiera hecho clic en un vínculo. Esto resulta útil para crear vínculos de adquisición manuales y controlar personalmente el redireccionamiento a la tienda de aplicaciones.

   * Esta es la sintaxis para este método:

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```