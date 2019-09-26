---
description: Puede configurar la aplicación para que utilice el servicio de notificaciones push de Apple (APNS) o Firebase Cloud Messaging (FCM).
keywords: móvil
seo-description: You can configure your app to use Apple Push Notification Service (APNS) or Firebase Cloud Messaging (FCM).
seo-title: Configure App to use APNS or FCM
solution: Marketing Cloud,Analytics
title: Configure App to use APNS or FCM
topic: Métricas
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: tm+mt
source-git-commit: 608384f1fee2a05699ff13fbd51c3cc43aeb693c

---


# Configure la aplicación para que utilice APNS o FCM{#configure-app-to-use-apns-or-fcm}

Puede configurar la aplicación para que utilice el servicio de notificaciones push de Apple (APNS) o Firebase Cloud Messaging (FCM).

## Aplicaciones de Android {#section_41D304102CDF4586911EC1413AD35A10}

### Si FCM no está activado en la aplicación

Para configurar la aplicación de Android para que utilice FCM en este escenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Haga clic en **[!UICONTROL Comenzar]** y seleccione **[!UICONTROL Agregar proyecto]**.

1. Introduzca un nombre de proyecto y, si selecciona Google Analytics para los datos de Firebase, haga clic en la casilla de verificación que acepta los términos controlador-controlador.

1. Haga clic en **[!UICONTROL Crear proyecto]** y espere a que se cree el proyecto.

1. Haga clic en el proyecto creado y se mostrará la página Información general **[!UICONTROL del]** proyecto para el proyecto creado. Haga clic en el botón con el icono de Android para añadir una aplicación de Android al proyecto.

1. Introduzca el nombre del paquete de la aplicación, el apodo de la aplicación y el certificado de firma si es necesario.

1. Siga los pasos adicionales sugeridos por el asistente de configuración. Después de comprobar la configuración de Firebase probando la comunicación con los servidores Firebase, vuelva a la página Información general **[!UICONTROL del]** proyecto.

1. Haga clic en el icono de engranaje situado a la derecha del botón Información general **[!UICONTROL del]** proyecto y haga clic en Configuración **[!UICONTROL del proyecto]**.

1. Haga clic en la ficha **[!UICONTROL Cloud Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Por ejemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Si FCM está activado en la aplicación

To configure your Android app to use FCM in this scenario:

1. Go to [https://firebase.google.com/](https://firebase.google.com/) and log in with your Google Dev credentials.

1. Haga clic en **[!UICONTROL Comenzar]**. Se abrirá la página de índice del proyecto. Busque el proyecto habilitado para Firebase que está vinculado a su aplicación de Android y haga clic en la tarjeta del proyecto.

1. Luego se debe cargar la Información general **[!UICONTROL del]** proyecto para el proyecto. Haga clic en el icono de engranaje situado a la derecha del botón Información general **[!UICONTROL del]** proyecto y haga clic en Configuración **[!UICONTROL del proyecto]**.

1. Haga clic en la ficha **[!UICONTROL Cloud Messaging]** .

1. Copy the **[!UICONTROL Legacy server key]** and **[!UICONTROL Sender ID]** for later use.

   Por ejemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## iOS apps {#section_2031DAB485FC4D2B9027E42AD90B294D}

Si desea configurar la aplicación de iOS para el uso de APNS:

1. Vaya a [https://developer.apple.com/account](https://developer.apple.com/account) e inicie sesión en su [cuenta para desarrolladores de Apple](https://developer.apple.com/account).
1. En **[!UICONTROL Aplicaciones de iOS]**, seleccione **[!UICONTROL Identificadores]**.
1. Si tiene un ID de aplicación configurado para la inserción, vaya al paso 11.
1. Press the **[!UICONTROL +]** button to create a new App ID.
1. Escriba la descripción del ID de aplicación.
1. Escriba el sufijo del ID de aplicación.

   >[!IMPORTANT]
   >
   >To support push, you must use an Explicit App ID that does **not** use a wild card (for example, `- com.tester.pushSample`).

1. En **[!UICONTROL Servicios de aplicación]**, seleccione la casilla **[!UICONTROL Notificaciones push]**.
1. Haga clic en **[!UICONTROL Continuar]**.
1. Haga clic en **[!UICONTROL Enviar]**.
1. Haga clic en **[!UICONTROL Finalizado]**.
1. Seleccione el ID de la aplicación que está configurada para utilizar la mensajería push desde la lista y haga clic en **[!UICONTROL Editar]**.
1. Si ya dispone de un certificado push, vaya al paso 15.
1. Desplácese hacia abajo hasta **[!UICONTROL Notificaciones push]** y haga clic en el botón **[!UICONTROL Crear certificado…]**.

   El botón en el que se hace clic depende de si se está creando un certificado para desarrollo o producción.
1. Siga los pasos para crear su CSR en el sitio web de Apple, cargar el CSR y generar el certificado.
1. Desplácese hacia abajo hasta la sección **[!UICONTROL Notificaciones push]** y descargue el certificado SSL que acaba de crear.
1. Double-click the downloaded certificate to add it to your keychain.

### SSL certificate and private keys

To get your SSL certificate and private key (APNS):

1. Abra **[!UICONTROL Acceso a Llaveros]**.
1. Haga clic en **[!UICONTROL Mis certificados]** y busque el **[!UICONTROL Certificado de servicios de iOS]** apropiado para su aplicación y su entorno.

   Puede identificar el certificado apropiado fijándose en el ID de paquete y en si es de desarrollo o de producción.

1. Expanda el certificado y verifique que contiene una clave privada.
1. Right-click the private key and select **[!UICONTROL Export "*`<name of key>`*]**.
1. Escriba la información necesaria en el cuadro de diálogo y guarde el nuevo `.p12` archivo.

   No tiene que escribir ninguna contraseña.

1. In the **[!UICONTROL Private Key]**, type the `.p12` file.

