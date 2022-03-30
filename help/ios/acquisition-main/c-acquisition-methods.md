---
description: 'La biblioteca iOS proporciona los siguientes métodos de adquisición '
solution: Experience Cloud Services,Analytics
title: Métodos de adquisición
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
exl-id: dd2721ae-b9a6-48b9-bc92-8e12ee551929
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# Métodos de adquisición  {#acquisition-methods}

La biblioteca iOS proporciona los siguientes métodos de adquisición:

Se admite el siguiente método:

* **acquisitionCampaignStartForApp:data:**

   Permite a los desarrolladores iniciar una campaña de adquisición de aplicación como si el usuario hubiera hecho clic en un vínculo. Esto resulta útil para crear vínculos de adquisición manuales y controlar personalmente el redireccionamiento al App Store, por ejemplo, mediante `SKStoreView`.

   * Esta es la sintaxis para este método:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Este es un ejemplo de código para este método:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```
