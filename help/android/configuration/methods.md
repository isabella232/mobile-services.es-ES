---
description: A continuación encontrará una lista de los métodos que proporciona la biblioteca de Android.
keywords: android;library;mobile;sdk
seo-description: A continuación encontrará una lista de los métodos que proporciona la biblioteca de Android.
seo-title: Métodos de configuración
solution: Experience Cloud,Analytics
title: Métodos de configuración
topic: Developer and implementation
uuid: 663aeb6c-1b97-4a3a-8c0e-dd4c2ec28c01
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 100%

---


# Métodos de configuración {#configuration-methods}

A continuación encontrará una lista de los métodos que proporciona la biblioteca de Android.

## Configuración inicial {#section_9169243ECC4744A899A8271F92090ECD}

Se debe llamar al método siguiente una vez que esté en el método `onCreate` de la actividad principal:

* `setContext`
Este es un ejemplo de código para este método:

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ```

## Configuración del SDK (clase Config) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * Registra un objeto que implementa la interfaz `AdobeDataCallback`. El método “llamada” sobrescrito se invocará con un valor `Config.MobileDataEvent` y con los datos asociados en un parámetro `Map<String, Object>` para el evento de activación. Para obtener más información sobre los eventos que activarán esta llamada de retorno, consulte *MobileDataEventEnum*.

      >[!TIP]
      >
      >Este método requiere la versión 4.9.0 o una posterior.

   * Esta es la sintaxis para este método:

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * Este es un ejemplo de código para este método:

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * Devuelve la versión actual de la biblioteca de Adobe Mobile.
   * Esta es la sintaxis para este método:

      ```java
      public static String getVersion();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * Devuelve la representación de enumeración del estado de privacidad del usuario actual.

      Estos son los valores de estado de privacidad:

      * `MOBILE_PRIVACY_STATUS_OPT_IN`, donde las visitas se envían inmediatamente.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, donde las visitas se descartan.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`, donde si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan).

         Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a incluido. El valor predeterminado se establece en el archivo `ADBMobileConfig.json`.
   * Esta es la sintaxis para este método:

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * Establece el estado de privacidad del usuario actual como `status`.

      Puede establecer el estado de privacidad en uno de los siguientes valores:
      * `MOBILE_PRIVACY_STATUS_OPT_IN`, donde las visitas se envían inmediatamente. Estas visitas se envían inmediatamente.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, donde las visitas se descartan. Estas visitas se descartan.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`, donde si el grupo de informes tiene habilitada la marca de fecha y hora, las visitas se guardan hasta que el estado de privacidad cambie a incluido (las visitas se envían) o excluido (las visitas se descartan).
Si el grupo de informes no tiene habilitada la marca de fecha y hora, las visitas se descartan hasta que el estado de privacidad cambie a incluido.
   * Esta es la sintaxis para este método:

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * Devuelve el valor de duración del usuario actual. El valor predeterminado es `0`.

   * Esta es la sintaxis para este método:

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * Este es un ejemplo de código para este método:

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * Si se ha establecido un identificador personalizado, se devuelve el identificador de usuario personalizado. Si no se ha establecido ningún identificador personalizado, devuelve `null`. El valor predeterminado es `null`.

      >[!TIP]
      >
      >Si la aplicación se actualiza del SDK 3.x al 4.x de Experience Cloud, el ID de visitante previo (personalizado o generado automáticamente) se recupera y se almacena como identificador de usuario personalizado. Esto preserva los datos de visitante al actualizar el SDK. Para las instalaciones nuevas en el SDK 4.x, hasta que esté establecido, el identificador de usuario será `null`.

   * Esta es la sintaxis para este método:

      ```java
      public static String&amp getUserIdentifier();
      ```

   * Este es el ejemplo de código para este método:

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * Establece el identificador de usuario como `identifier`.
   * Esta es la sintaxis para este método:

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * Devuelve la preferencia de registro de depuración actual. El valor predeterminado es `false`.
   * Esta es la sintaxis para este método:

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * Establece la preferencia de registro de depuración en `debugLogging`.
   * Esta es la sintaxis para este método:

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * Indica al SDK que los datos del ciclo vital deben ser recopilados para su uso en todas las soluciones en el SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/configuration/methods.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      Con datos de contexto extra:

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * (**Versión 4.2 o posterior**) Indica al SDK que se deben recopilar los datos del ciclo vital para su uso en todas las soluciones del SDK. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).
   * Esta es la sintaxis para este método:

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * Este es un ejemplo de código para este método:

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
      ```

* **pauseCollecting&#x200B;LifecycleData**

   * Indica al SDK que la aplicación está en pausa, para que las métricas del ciclo vital se calculen correctamente. Por ejemplo, `onPause` recopila una marca de fecha y hora para determinar la duración de la sesión anterior. Esto también establece un indicador para que el ciclo de duración sepa que la aplicación no se bloqueó. Para obtener más información, consulte [Métricas del ciclo vital](/help/android/metrics.md).

   * Esta es la sintaxis para este método:

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**Versión 4.2 o posterior**) Se configura el icono pequeño que se utilizará para las notificaciones creadas por el SDK. Este icono aparecerá en la barra de estado y es la imagen secundaria que se muestra cuando el usuario ve la notificación completa en el centro de notificaciones.
   * Esta es la sintaxis para este método:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**Versión 4.2 o posterior**) Se configura el icono grande que se utilizará para las notificaciones creadas por el SDK. Este icono es la imagen principal que se muestra cuando el usuario ve la notificación completa en el centro de notificaciones.
   * Esta es la sintaxis para este método:

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * Este es un ejemplo de código para este método:

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**Versión 4.2 o posterior**) Le permite cargar un archivo de configuración JSON ADBMobile diferente cuando se inicia la aplicación. Se utiliza la configuración distinta hasta que se cierre la aplicación.
   * Esta es la sintaxis para este método:

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * Este es un ejemplo de código para este método:

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * Establece el token del dispositivo para notificaciones push.
   * Esta es la sintaxis para este método:

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * Este es un ejemplo de código para este método:

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * Proporciona al SDK un elemento al que llamar que devuelve la cadena del identificador de publicidad que Google Play Services devuelve. El SDK ejecuta esta tarea en un subproceso en segundo plano y establece para el identificador de publicidad una variable interna que se basa en el valor devuelto por el elemento al que llamar.

      >[!IMPORTANT]
      > 
      >Si desea utilizar el identificador de publicidad para la adquisición o el ciclo de duración, llámele antes de llamar a `Config.collectLifecycleData`.

      * Esta es la sintaxis para este método:

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * Este es un ejemplo de código para este método:

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## Interfaz de AdobeDataCallback {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
