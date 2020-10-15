---
description: Puede configurar su aplicación para que utilice el servicio de notificaciones push de Apple (APNS) o la mensajería de Firebase Cloud (FCM).
keywords: mobile
seo-description: Puede configurar su aplicación para que utilice el servicio de notificaciones push de Apple (APNS) o la mensajería de Firebase Cloud (FCM).
seo-title: Configurar las aplicaciones para utilizar APNS o FCM
solution: Experience Cloud,Analytics
title: Configurar las aplicaciones para utilizar APNS o FCM
topic: Metrics
uuid: fa411f2a-ba47-4499-bbe5-1aedef6b49ad
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '652'
ht-degree: 100%

---


# Configure la aplicación para que utilice APNS o FCM {#configure-app-to-use-apns-or-fcm}

Puede configurar su aplicación para que utilice el servicio de notificaciones push de Apple (APNS) o la mensajería de Firebase Cloud (FCM).

## Aplicaciones de Android {#section_41D304102CDF4586911EC1413AD35A10}

### Si FCM no está activado en la aplicación

Para configurar la aplicación de Android para que utilice FCM en este escenario:

1. Vaya a [https://firebase.google.com/](https://firebase.google.com/) e inicie sesión con sus credenciales de desarrollador de Google.

1. Haga clic en **[!UICONTROL Comenzar]** y seleccione **[!UICONTROL Agregar proyecto]**.

1. Introduzca un nombre de proyecto y, si selecciona Google Analytics para los datos de Firebase, haga clic en la casilla de verificación que acepta los términos de controlador a controlador.

1. Haga clic en **[!UICONTROL Crear proyecto]** y espere a que se cree el proyecto.

1. Haga clic en el proyecto creado y se mostrará la página **[!UICONTROL Información general del proyecto]** para el proyecto creado. Haga clic en el botón con el icono de Android para añadir una aplicación de Android al proyecto.

1. Introduzca el nombre del paquete de la aplicación, el apodo de la aplicación y el certificado de firma si es necesario.

1. Siga los pasos adicionales sugeridos por el asistente de configuración. Después de comprobar la configuración de Firebase probando la comunicación con los servidores Firebase, vuelva a la página **[!UICONTROL Información general del proyecto]**.

1. Haga clic en el icono de engranaje situado a la derecha del botón **[!UICONTROL Información general del proyecto]** y haga clic en **[!UICONTROL Configuración del proyecto]**.

1. Haga clic en la pestaña **[!UICONTROL Mensajería de Cloud]**.

1. Copie la **[!UICONTROL Clave del servidor heredado]** y el **[!UICONTROL ID de remitente]** para usarlos más adelante.

   Por ejemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```

### Si FCM está activado en la aplicación

Para configurar la aplicación de Android para que utilice FCM en este escenario:

1. Vaya a [https://firebase.google.com/](https://firebase.google.com/) e inicie sesión con sus credenciales de desarrollador de Google.

1. Haga clic en **[!UICONTROL Comenzar]**. Se abrirá la página de índice del proyecto. Busque el proyecto habilitado para Firebase que está vinculado a su aplicación de Android y haga clic en la tarjeta del proyecto.

1. Luego se debe cargar la **[!UICONTROL Información general del proyecto]** para el proyecto. Haga clic en el icono de engranaje situado a la derecha del botón **[!UICONTROL Información general del proyecto]** y haga clic en **[!UICONTROL Configuración del proyecto]**.

1. Haga clic en la pestaña **[!UICONTROL Mensajería de Cloud]**.

1. Copie la **[!UICONTROL Clave del servidor heredado]** y el **[!UICONTROL ID de remitente]** para usarlos más adelante.

   Por ejemplo:

   ```
   - Legacy server key = AIzaSyC6FNgsCOpBL5eXhDvwf8979mWba6x7Roo
   ```

   ```
   - Sender ID = 835015092250
   ```



## Aplicaciones de iOS {#section_2031DAB485FC4D2B9027E42AD90B294D}

Si desea configurar la aplicación de iOS para el uso de APNS:

1. Vaya a [https://developer.apple.com/account](https://developer.apple.com/account) e inicie sesión en su [cuenta de desarrollador de Apple](https://developer.apple.com/account).
1. En **[!UICONTROL Aplicaciones de iOS]**, seleccione **[!UICONTROL Identificadores]**.
1. Si dispone de un ID de aplicación configurado para la funcionalidad push, vaya al paso 11.
1. Pulse el botón **[!UICONTROL +]** para crear un nuevo ID de aplicación.
1. Escriba una descripción del ID de la aplicación.
1. Escriba un sufijo de ID de aplicación.

   >[!IMPORTANT]
   >
   >Para ser compatible con la funcionalidad push, debe utilizar un ID de aplicación explícito que **no** utilice comodines (por ejemplo,`- com.tester.pushSample`).

1. En **[!UICONTROL Servicios de aplicación]**, seleccione la casilla **[!UICONTROL Notificaciones push]**.
1. Haga clic en **[!UICONTROL Continuar]**.
1. Haga clic en **[!UICONTROL Enviar]**.
1. Haga clic en **[!UICONTROL Finalizado]**.
1. Seleccione el ID de la aplicación que está configurada para utilizar la mensajería push desde la lista y haga clic en **[!UICONTROL Editar]**.
1. Si ya dispone de un certificado push, vaya al paso 15.
1. Desplácese hacia abajo hasta **[!UICONTROL Notificaciones push]** y haga clic en el botón **[!UICONTROL Crear certificado…]**

   El botón en el que hace clic depende de si se está creando un certificado para desarrollo o producción.
1. Siga los pasos para crear su CSR en el sitio web de Apple, cargarlo y generar el certificado.
1. Desplácese hacia abajo hasta la sección **[!UICONTROL Notificaciones push]** y descargue el certificado SSL que acaba de crear.
1. Haga doble clic en el certificado descargado para agregarlo al llavero.

### Certificado SSL y claves privadas

Para obtener el certificado SSL y la clave privada (APNS):

1. Abra **[!UICONTROL Acceso a Llaveros]**.
1. Haga clic en **[!UICONTROL Mis certificados]** y busque el **[!UICONTROL Certificado de servicios de iOS]** apropiado para su aplicación y su entorno.

   Puede identificar el certificado correcto haciendo coincidir el ID del paquete y si se trata de desarrollo o producción.

1. Expanda el certificado y compruebe que contiene una clave privada.
1. Haga clic con el botón derecho en la clave privada y seleccione **[!UICONTROL Exportar &quot;*`<name of key>`*]**.
1. Escriba la información necesaria en el cuadro de diálogo y guarde el nuevo archivo `.p12`.

   No tiene que escribir ninguna contraseña.

1. En **[!UICONTROL Clave privada]**, escriba el nombre del archivo `.p12`.

