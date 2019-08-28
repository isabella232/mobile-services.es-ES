---
description: 'La biblioteca iOS proporciona los siguientes métodos de adquisición '
seo-description: 'La biblioteca iOS proporciona los siguientes métodos de adquisición '
seo-title: Métodos de adquisición
solution: Marketing Cloud, Analytics
title: Métodos de adquisición
uuid: 6 f 88 de 57-793 d -4 d 33-9 a 54-f 6714289 fd 2 c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

La biblioteca iOS proporciona los siguientes métodos de adquisición:

Se admite el método siguiente:

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

