---
product: Adobe Campaign
title: Integrera Campaign SDK:er med er app
description: Lär dig hur du integrerar Campaign Android och iOS SDK med din app
version: v8
feature: Push
role: Developer
level: Experienced
hide: true
hidefromtoc: true
source-git-commit: f1a854c6aa91755add4dfe422879ffd12e8d297b
workflow-type: tm+mt
source-wordcount: '1283'
ht-degree: 1%

---

# Integrera Campaign SDK:er med er app {#integrate-campaign-sdk}

Använd Campaign SDK för iOS och Android för att underlätta integreringen av mobilapplikationen i Adobe Campaign.

Versioner som stöds av Android och iOS, samt kompatibla versioner av Campaign SDK för Campaign v8, listas i [kompatibilitetsmatrisen](../start/compatibility-matrix.md#MobileSDK).

>[!NOTE]
>
>Som Campaign-administratör kan du hämta SDK:er för kampanjer från [Experience Cloud Software Distribution](https://experience.adobe.com/#/downloads/content/software-distributicampaign.html). Mer information får du om du kontaktar [Adobe kundtjänst](https://helpx.adobe.com/sv/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Deklarera integreringsinställningar {#declaring-integration-settings}

För att integrera Campaign SDK i mobilappen måste den funktionella administratören lämna följande information till utvecklaren:

* **En integreringsnyckel**: för att göra det möjligt för Adobe Campaign-plattformen att identifiera mobilapplikationen.

   >[!NOTE]
   >
   >Integreringsnyckeln anges i Adobe Campaign-konsolen på fliken **[!UICONTROL Information]** för tjänsten som är avsedd för mobilprogrammet. Mer information finns i [dokumentationen för Campaign Classic v7](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application.html?lang=en#creating-ios-app).

* **En spårnings-URL**: som matchar adressen för Adobe Campaign-spårningsservern.
* **En marknadsförings-URL**: för att aktivera insamling av prenumerationer.

* **I Android**:

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
   ```

* **I iOS**:

   ```
   Neolane_SDK *nl = [Neolane_SDK getInstance];
   [nl setMarketingHost:strMktHost];
   [nl setTrackingHost:strTckHost];
   [nl setIntegrationKey:strIntegrationKey];
   ```

## Integrera Android SDK

Android SDK är ett jar-bibliotek skrivet i JAVA. Med den kan Android-utvecklare integrera med Adobe Campaign: registrera en ny enhet, länka enheten till en användare, spåra beteende och mycket annat.

I det här avsnittet får du lära dig hur du använder Android SDK i ett Android-program som implementerar [Google Firebase Cloud Messaging (FCM)](https://firebase.google.com/docs/cloud-messaging/).

### Konfigurera FCM

Om du vill använda push-meddelandet på Android måste du ha ett FCM-konto, konfigurera ditt Android-program så att du får meddelandet och länka programmet till FCM-kontot. Läs mer i [Google Documentation](https://firebase.google.com/docs/cloud-messaging/).

Läs [Google Documentation](https://firebase.google.com/docs/android/setup) om du vill lägga till Firebase i ditt Android-projekt.

Lär dig hur du implementerar FCM i ditt program i [Google Documentation](https://firebase.google.com/docs/android/setup).

>[!NOTE]
>
> * Glöm inte att hämta och lägga till google-services.json i ditt projekt.
   >
   > 
* `apiKey` måste matcha uppsättningen `projectKey` i det Adobe Campaign-mobilprogram som är länkat till det här Android-programmet.


### Konfigurera Android SDK

1. **Initiera SDK**

   Innan du använder Android SDK måste du initiera det. SDK-initieringen kan göras i funktionen `onCreate` för en aktivitet.

   ```
   /** Called when the activity is first created. */
   @Override
   public void onCreate(Bundle savedInstanceState)
   {
       super.onCreate(savedInstanceState);
   
       // initialize Neolane sdk
       SharedPreferences settings = getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
   
       Neolane.getInstance().setIntegrationKey(settings.getString(YourApplicationActivity.APPUUID_NAME, YourApplicationActivity.DFT_APPUUID));
       Neolane.getInstance().setMarketingHost(settings.getString(YourApplicationActivity.SOAPRT_NAME, YourApplicationActivity.DFT_SOAPRT));
       Neolane.getInstance().setTrackingHost(settings.getString(YourApplicationActivity.TRACKRT_NAME, YourApplicationActivity.DFT_TRACKRT));
       ...
   }
   ```

   `IntegrationKey` måste matcha med IntegrationKey-uppsättningen i det Adobe Campaign Mobile-program som är länkat till det här Android-programmet.

2. **Registrera den mobila enheten på Adobe Campaign-servern**

   Registreringsfunktionen gör att du kan:

   * skicka meddelande-ID eller push-ID (deviceToken för iOS och registrationID för Android) till Adobe Campaign.
   * återskapa avstämningsnyckeln eller userKey (till exempel e-post eller kontonummer)

   Du måste registrera enheten hos Adobe Campaign, vid programinitieringen eller vid en användaråtgärd. Det kan du enkelt göra med metoden `registerDevice`.

   ```
   public void onClick(View v)
   {
   SharedPreferences settings = this.context.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
   EditText mailEdit = (EditText) this.context.findViewById(R.id.editText1);
   
   final String FCMRegistrationId = FirebaseInstanceId.getInstance().getToken();
   if (FCMRegistrationId != null)
       NeoTripActivity.registerOnNeolane(this.context, FCMRegistrationId, mailEdit.getText().toString());
   
   }
   ```

   YourApplicationActivity.java

   ```
   public static void registerOnNeolane(final Context ctx, String registrationId, String userKey)
   {
       NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
       // Additional Subscription Parameters
       Map<String,Object> additionnalParam = new HashMap<String, Object>();
       additionnalParam.clear();
       SharedPreferences settings = ctx.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
       if (settings.getBoolean(YourApplicationActivity.SUBPARAMEN1_NAME, false))
       {
           additionnalParam.put(settings.getString(YourApplicationActivity.SUBPARAMNAME1_NAME, "") , settings.getString(YourApplicationActivity.SUBPARAMVALUE1_NAME, ""));   
       }
       if (settings.getBoolean(YourApplicationActivity.SUBPARAMEN2_NAME, false))
       {
           additionnalParam.put(settings.getString(YourApplicationActivity.SUBPARAMNAME2_NAME, "") , settings.getString(YourApplicationActivity.SUBPARAMVALUE2_NAME, ""));   
       }
       if ( additionnalParam.isEmpty() )
       {
           additionnalParam = null;
       }
       // Neolane Registration
       neolaneAs.registerDevice(registrationId, userKey, additionnalParam, ctx, new RequestListener() {
       public void onComplete(String e, Object obj)
       {
           Intent upd = new Intent();
           upd.setAction(BROADCAST_NEWREGISTER_ACTION);
           ctx.sendBroadcast(upd);
       }
   
       public void onNeolaneException(NeolaneException e, Object obj)
       {
           sendErrorMsg(e.getErrorString());
       }
   
       public void onIOException(IOException e, Object obj)
       {
           sendErrorMsg(e.getMessage());
       }
   
       public void sendErrorMsg(String err)
       {
           SharedPreferences.Editor edit = ctx.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE).edit();
           edit.putBoolean(YourApplicationActivity.REGISTRATION_ERROR_NEOLANE_KEYNAME, true);
           edit.commit();
           Intent toast = new Intent();
           toast.setAction(BROADCAST_TOAST_DISPLAY_TEXT);
           toast.putExtra("text", "An error happened, please register again (" + err + ")");
           ctx.sendBroadcast(toast);
       }
       });
   }
   ```

1. **Meddela Campaign när användarens mobilenhetstoken ändras**

   Vi rekommenderar att du använder funktionen `registerDevice` när du anropar funktionen `onTokenRefresh` för att meddela Adobe Campaign om ändringen i användarens mobilenhetstoken.

   Exempel:

   YourApplicationFirebaseInstanceIDService.java

   ```
   package com.android.YourApplication;
   
   import android.content.Context;
   import android.content.SharedPreferences;
   import android.util.Log;
   
   import com.google.firebase.iid.FirebaseInstanceId;
   import com.google.firebase.iid.FirebaseInstanceIdService;
   
   import static android.content.SharedPreferences.*;
   
   public class YourApplicationFirebaseInstanceIDService extends FirebaseInstanceIdService 
   {
       @Override
       public void onTokenRefresh() 
       {
       SharedPreferences settings = getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
       if (!settings.getBoolean(YourApplicationActivity.USE_GCM, false))
           {
           String refreshedToken = FirebaseInstanceId.getInstance().getToken();
           String userKey = settings.getString(YourApplicationActivity.USERKEY_NAME, "");
           Editor edit = settings.edit();
           edit.putString(YourApplicationActivity.FCM_REGISTRATIONID_NAME, refreshedToken);
           edit.commit();
           YourApplicationActivity.registerOnNeolane(this, refreshedToken, userKey);
           }
       }
   }
   ```

1. **Konfigurera Firebase Messaging Service**

   Utöka `FirebaseMessagingService` i `onMessageReceived`-återanropet för att ta emot meddelanden. Vi rekommenderar att du anropar funktionen `notifyReceive` när återanropet `onMessageReceived` anropas för att aktivera spårning av meddelandemottagningen på den mobila enheten. I Adobe Campaign heter detta **print**-meddelande: den här funktionen ska anropas precis innan operativsystemet begär att meddelandet ska visas.

   YourApplicationMessagingService.java

   ```
   package com.android.YourApplication;
   
   import android.content.Context;
   import android.content.SharedPreferences;
   import android.os.Bundle;
   import android.util.Log;
   
   import com.google.firebase.messaging.FirebaseMessagingService;
   import com.google.firebase.messaging.RemoteMessage;
   
   import java.util.Iterator;
   import java.util.Map;
   import java.util.Map.Entry;
   
   public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService 
       {
       private static final String TAG = "MyFirebaseMsgService";
   
       @Override
       public void onMessageReceived(RemoteMessage message) 
           {
           Log.d(TAG, "Receive message from: " + message.getFrom());
           Map<String,String> payloadData = message.getData();
           final Bundle extras = new Bundle();
           final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
           while(iter.hasNext())
           {
           final Entry<String, String>  entry =iter.next();
           extras.putString(entry.getKey(), entry.getValue());
           }
   
           SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
           String mesg = payloadData.get("_msg");
           String title = payloadData.get("title");
           String url = payloadData.get("url");
           String messageId = payloadData.get("_mId");
           String deliveryId = payloadData.get("_dId");
           YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
           }
       }   
   ```

   För Campaign Android SDK v1.1.1

   ```
   public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras)
   {
       if( message == null ) message = "No Content";
       if( title == null )   title = "No title";
       if( url == null )     url = "http://www.tripadvisor.fr";
       int iconId = R.drawable.notif_neotrip;
   
       // notify Adobe Campaign that a notification just arrived
       SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
       Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
       Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
       Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
   
       NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
       nas.notifyReceive(messageId, deliveryId, new NeolaneAsyncRunner.RequestListener() {
       public void onNeolaneException(NeolaneException arg0, Object arg1) {}
       public void onIOException(IOException arg0, Object arg1) {}
       public void onComplete(String arg0, Object arg1){}
       });
       if (yourApplication.isActivityVisible())
       {
       Log.i("INFO", "The application has the focus" );
       ...
       }
       else
       {
       // notification creation
       NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
       Notification notification;
   
       // Activity to start
       Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
       notifIntent.putExtra("notificationText", message);
       notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
       notifIntent.putExtra("_dId", deliveryId);
       notifIntent.putExtra("_mId", messageId);
       notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
       PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);
   
       notification = new Notification.Builder(context)
               .setContentTitle(title)
               .setContentText(message)
               .setSmallIcon(iconId)
               .setContentIntent(contentIntent)
               .build();
   
       // launch the notification
       notification.flags |= Notification.FLAG_AUTO_CANCEL;
       notificationManager.notify(1234, notification);
       }
   }
   ```

1. **Spåra öppningar av datameddelanden**

   För datameddelanden kan du spåra när en användare klickar på ett meddelande för att öppna det med funktionen `notifyOpening`. Meddelandeaktiviteten skapas när användaren klickar på meddelandet (skapas under `onMessageReceived`funktionsanropet)

   För Campaign Android SDK v1.1.1

   ```
   public class NotificationActivity extends Activity {
       public void onCreate(Bundle savedBundle) {
           [...]
           Bundle extra = getIntent().getExtras();
           if (extra != null) {
               // reinit the Campaign sdk
               SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
               Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
               Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));               
               Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
   
               // Get the messageId and the deliveryId to perform tracking
               String deliveryId = extra.getString("_dId");
               String messageId = extra.getString("_mId");
   
               if (deliveryId != null && messageId != null) 
               {
                   try {
                   Neolane.getInstance().notifyOpening(messageId, Integer.valueOf(deliveryId));
                   } catch (NeolaneException e) {
                   // ...
                   } catch (IOException e) {
                   // ...
                   }
               }
           }
       }
   }
   
1. **Spåra öppningar och klicka på meddelandemeddelanden**

   För meddelandena måste spårning av öppnings-/klickningar utföras med funktionen `notifyOpening` i programstartaktiviteten enligt nedan:

   ```
   /** Called when the activity is first created. */
       @Override
       public void onCreate(Bundle savedInstanceState)
       {
       super.onCreate(savedInstanceState);
   
       SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
   
       // initialize Neolane sdk
       Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
       Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
       Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
       ...
       ...
       ...
   
           // Manage opening/receive tracking of message notification
           Intent intent = getIntent();
           Bundle data = intent.getExtras();
           String messageId = null, deliveryId = null;
           if( data != null ) {
           if (data.containsKey("_mId")) messageId = data.get("_mId").toString();
           if (data.containsKey("_dId")) deliveryId = data.get("_dId").toString();
           if ( messageId != null && deliveryId != null) {
               Log.i(TAG, "Notify opening from backgroun click_action");
               NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
               nas.notifyOpening(messageId, deliveryId, new NeolaneAsyncRunner.RequestListener() {
               public void onNeolaneException(NeolaneException arg0, Object arg1) {
                   toastMessage( "error", getString(R.string.open_track_sdk_error) + arg0.getErrorCode());
               }
               public void onIOException(IOException arg0, Object arg1) {
                   toastMessage( "error", getString(R.string.open_track_io_error) +  arg0.getLocalizedMessage());
               }
               public void onComplete(String arg0, Object arg1) {
                   toastMessage( "error", getString(R.string.open_track_ok));
               }
               });
               nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
               public void onNeolaneException(NeolaneException arg0, Object arg1) {
                   toastMessage( "error", getString(R.string.rec_track_sdk_error) + arg0.getErrorCode());
               }
               public void onIOException(IOException arg0, Object arg1) {
                   toastMessage( "error", getString(R.string.rec_track_io_error) +  arg0.getLocalizedMessage());
               }
               public void onComplete(String arg0, Object arg1) {
                   toastMessage( "error", getString(R.string.rec_track_ok));
               }
               });
           }
           }
       }
   ```

>[!NOTE]
>
> Liknande hantering måste utföras om användaren använder alternativet `click_action` i målaktiviteten.


1. **Ta emot spårning för datameddelanden**

   För datameddelanden tas spårningen emot på anropsnivå `onMessageReceived`. Funktionen notifyReceive måste anropas.

   YourApplicationMessagingService.java

   ```
   package com.android.YourApplication;
   
   import android.content.Context;
   import android.content.SharedPreferences;
   import android.os.Bundle;
   import android.util.Log;
   
   import com.google.firebase.messaging.FirebaseMessagingService;
   import com.google.firebase.messaging.RemoteMessage;
   
   import java.util.Iterator;
   import java.util.Map;
   import java.util.Map.Entry;
   
   
   public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
   private static final String TAG = "MyFirebaseMsgService";
   
   @Override
   public void onMessageReceived(RemoteMessage message) 
       {
           Log.d(TAG, "Receive message from: " + message.getFrom());
           Map<String,String> payloadData = message.getData();
           final Bundle extras = new Bundle();
           final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
           while(iter.hasNext())
           {
           final Entry<String, String>  entry =iter.next();
           extras.putString(entry.getKey(), entry.getValue());
           }
   
           SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
           String mesg = payloadData.get("_msg");
           String title = payloadData.get("title");
           String url = payloadData.get("url");
           String messageId = payloadData.get("_mId");
           String deliveryId = payloadData.get("_dId");
           YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
       }
   }
   ```

   ```
   public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
       .....
       .....
           // notify Neolane that a notification just arrived
           SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
           Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
           Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
           Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
   
           NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
           nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
               public void onNeolaneException(NeolaneException arg0, Object arg1) {}
               public void onIOException(IOException arg0, Object arg1) {}
               public void onComplete(String arg0, Object arg1){}
       });
   }
   ```

1. **Ta emot spårning för aviseringsmeddelanden**

   För meddelanden måste spårningsmottagningen konfigureras på två nivåer:

   * `onMessageReceived` (program som inte finns i bakgrunden): implementeringen har gjorts i föregående avsnitt
   * `onCreate` för startaktiviteten (eller målaktiviteten om  `click_action`funktionen används). (Programmet är inte i bakgrunden).

   Det måste göras samtidigt som du spårar genom att öppna/klicka.

   ```
   /** Called when the activity is first created. */
       @Override
       public void onCreate(Bundle savedInstanceState)
       {
           super.onCreate(savedInstanceState);
   
           SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
   
           // initialize Neolane sdk
           Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
           Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
           Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
   ...
   ...
   ...
   
       // Manage opening/receive tracking of message notification
       Intent intent = getIntent();
       Bundle data = intent.getExtras();
       String messageId = null, deliveryId = null;
       if( data != null ) {
       if (data.containsKey("_mId")) messageId = data.get("_mId").toString();
       if (data.containsKey("_dId")) deliveryId = data.get("_dId").toString();
       if ( messageId != null && deliveryId != null) {
           Log.i(TAG, "Notify opening from backgroun click_action");
           NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
           nas.notifyOpening(messageId, deliveryId, new NeolaneAsyncRunner.RequestListener() {
           public void onNeolaneException(NeolaneException arg0, Object arg1) {
               toastMessage( "error", getString(R.string.open_track_sdk_error) + arg0.getErrorCode());
           }
           public void onIOException(IOException arg0, Object arg1) {
               toastMessage( "error", getString(R.string.open_track_io_error) +  arg0.getLocalizedMessage());
           }
           public void onComplete(String arg0, Object arg1) {
               toastMessage( "error", getString(R.string.open_track_ok));
           }
           });
           nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
           public void onNeolaneException(NeolaneException arg0, Object arg1) {
               toastMessage( "error", getString(R.string.rec_track_sdk_error) + arg0.getErrorCode());
           }
           public void onIOException(IOException arg0, Object arg1) {
               toastMessage( "error", getString(R.string.rec_track_io_error) +  arg0.getLocalizedMessage());
           }
           public void onComplete(String arg0, Object arg1) {
               toastMessage( "error", getString(R.string.rec_track_ok));
           }
           });
       }
       }
   }
   ```


## Integrera iOS SDK

1. **Registrera den mobila enheten på Adobe Campaign-servern**

   Registreringsfunktionen gör att du kan:

   * skicka meddelande-ID eller push-ID (deviceToken för iOS och registrationID för Android) till Adobe Campaign.
   * återskapa avstämningsnyckeln eller userKey (till exempel e-post eller kontonummer)

   ```
   // Callback called on successful registration to the APNs
    - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
   {
     // Pass the token to Adobe Campaign
     Neolane_SDK *nl = [Neolane_SDK getInstance];
     [nl registerDevice:tokenString:self.userKey:dic];
   }
   ```

1. **Aktivera spårningsfunktion**

Med spårningsfunktionen kan du spåra när meddelanden aktiveras (öppnas).

```
(void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
*nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
...  
completionHandler(UIBackgroundFetchResultNoData);
}
```

1. **Spårning av tyst meddelande**

   Med iOS kan du skicka tysta meddelanden, ett meddelande eller data som skickas direkt till ett mobilprogram utan att det visas. Med Adobe Campaign kan du spåra dem.

   Följ exemplet nedan för att spåra ditt tysta meddelande:

   ```
   // AppDelegate.m
   ...
   ...
   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   ...
   ...
   // Callback called when the application is already launched (whether the application is running foreground or background)
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
   {
   NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
   if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
   NSLog(@"Application state: %ld", (long)application.applicationState);
   
   // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
   if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
   NSLog(@"Silent Push Notification");
   ...  
   ...
   //Call receive tracking
           Neolane_SDK *nl = [Neolane_SDK getInstance];
   [nl track:launchOptions:NL_TRACK_RECEIVE];
   
   completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
   return;
   }  
   ...
   ...
           completionHandler(UIBackgroundFetchResultNoData);
   }
   ```

1. Konfigurera registreringsstatus

   Delegatprotokollet gör att du kan få resultatet av anropet **registerDevice** och kan användas för att ta reda på om ett fel uppstod under registreringen.

   Prototypen **registerDeviceStatus** är:

   ```
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
   ```

   * **Med** Status kan du veta om en registrering lyckades eller om ett fel uppstod.

   * **** ErrorReasonger dig mer information om de fel som uppstod. Mer information om tillgängliga fel och deras beskrivningar finns i tabellen nedan.

   <table> 
    <thead>
    <tr>
    <th> Status<br /> </th>
    <th> Beskrivning<br /> </th>
    <th> ErrorReason<br /> </th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td> ACCRegisterDeviceStatusSuccess <br /> </td>
    <td> Registreringen lyckades<br /> </td>
    <td> TOM<br /> </td>
    </tr>
    <tr> 
    <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
    <td> Värdnamnet för ACC-marknadsföringsservern är tomt eller inte inställt.<br /> </td>
    <td> TOM<br /> </td>
    </tr>
    <tr> 
    <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
    <td> Integreringsnyckeln är tom eller inte inställd.<br /> </td>
    <td> TOM<br /> </td>
    </tr>
    <tr> 
    <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
    <td> Anslutningsproblem med ACC<br /> </td>
    <td> Mer information (på operativsystemets aktuella språk)<br /> </td>
    </tr>
    <tr> 
    <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
    <td> Angivet UUID (integrationsnyckel) är okänt.<br /> </td>
    <td> TOM<br /> </td>
    </tr>
    <tr> 
    <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
    <td> Ett oväntat fel returnerades till ACC-servern.<br /> </td>
    <td> Felmeddelandet returnerades till ACC.<br /> </td>
    </tr>
    </tbody>
    </table>

   **Definitionen av Neolane_** SDKDelegateprotocol och  **** registerDeviceStatusdelegate är följande:

   ```
   //  Neolane_SDK.h
   //  Neolane SDK
   ..
   .. 
   // Register Device Status Enum
   typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
   ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
   ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The Campaign marketing server hostname is Empty or not set
   ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
   ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with Campaign, more information in errorReason
   ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
   ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by Campaign server, more information in errorReason
   };
   // define the protocol for the registerDeviceStatus delegate
   @protocol Neolane_SDKDelegate <NSObject>
   @optional
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
   @end
   @interface Neolane_SDK: NSObject {
   } 
   ...
   ...
   // registerDeviceStatus delegate
   @property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
   ...
   ...
   @end
   ```

   Så här implementerar du **registerDeviceStatus**-delegaten:

   1. Implementera **setDelegate** under SDK-initieringen.

      ```
      // AppDelegate.m
      ...
      ... 
      - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
      {
      ...
      ...
          // Get the stored settings
      
          NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
          NSString *strMktHost = [defaults objectForKey:@"mktHost"];
          NSString *strTckHost = [defaults objectForKey:@"tckHost"];
          NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
          userKey = [defaults objectForKey:@"userKey"];
      
          // Configure Neolane SDK on first launch
          Neolane_SDK *nl = [Neolane_SDK getInstance];
          [nl setMarketingHost:strMktHost];
          [nl setTrackingHost:strTckHost];
          [nl setIntegrationKey:strIntegrationKey];
          [nl setDelegate:self];    // HERE
      ...
      ...
      }
      ```

   1. Lägg till protokollet i **@interface** för klassen.

      ```
      //  AppDelegate.h
      
      #import <UIKit/UIKit.h>
      #import <CoreLocation/CoreLocation.h>
      #import "Neolane_SDK.h"
      
      @class LandingPageViewController;
      
      @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
          CLLocationManager *locationManager;
          NSString *userKey;
          NSString *mktServerUrl;
          NSString *tckServerUrl;
          NSString *homeURL;
          NSString *strLandingPageUrl;
          NSTimer *timer;
      }
      ```

   1. Implementera delegaten i **AppDelegate**.

      ```
      //  AppDelegate.m
      
      #import "AppDelegate.h"
      #import "Neolane_SDK.h"
      #import "LandingPageViewController.h"
      #import "RootViewController.h"
      ...
      ...
      - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
      {
          NSLog(@"registerStatus: %lu",status);
      
          if ( errorReason != nil )
              NSLog(@"errorReason: %@",errorReason);
      
          if( status == ACCRegisterDeviceStatusSuccess )
          {
              // Registration successful
              ...
              ...
          }
          else { // An error occurred
              NSString *message;
              switch ( status ){
                  case ACCRegisterDeviceStatusFailureUnknownUUID:
                      message = @"Unkown IntegrationKey (UUID)";
                      break;
                  case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                      message = @"Marketing URL not set or Empty";
                      break;
                  case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                      message = @"Integration Key not set or empty";
                      break;
                  case ACCRegisterDeviceStatusFailureConnectionIssue:
                      message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                      break;
                  case ACCRegisterDeviceStatusFailureUnexpectedError:
                  default:
                      message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                      break;
              }
          ...
          ...
          }
      }
      @end
      ```


## Variabler {#variables}

Med variablerna kan du definiera mobilprogrammets beteende efter att ha tagit emot ett meddelande. Dessa variabler måste definieras i mobilprogramkoden och i Adobe Campaign-konsolen på fliken **[!UICONTROL Variables]** i den dedikerade mobilprogramtjänsten.

[!DNL :arrow_upper_right:] Läs mer i  **Campaign Classic v7-** dokumentationen om mobilappen:  [Konfigurationssteg för ](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application.html) iOS- och  [konfigurationssteg för Andoid](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/configure-the-mobile-app/configuring-the-mobile-application-android.html).

Nedan visas ett exempel på en kod som gör att ett mobilprogram kan samla in tillagda variabler i ett meddelande. I vårt exempel använder vi variabeln&quot;VAR&quot;.

* **I Android**:

   ```
   public void onReceive(Context context, Intent intent) {
        ...
       String event = intent.getStringExtra("VAR");
        ...
   }
   ```

* **I iOS**:

   ```
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
       ....
       if( launchOptions )
       {
           // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
           NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
           if( localLaunchOptions )
           {
            ...
            [localLaunchOptions objectForKey:@"VAR"];
           ...
           }
      }
   }
   
   // Callback called when the application is already launched (whether the application is running foreground or background)
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
   {
       if( launchOptions )
       {
        ...
           [launchOptions objectForKey:@"VAR"];
       }
   }
   ```

>[!CAUTION]
>
>Adobe rekommenderar att du väljer korta variabelnamn eftersom meddelandestorleken är begränsad till 4kB för iOS och Android.

## Meddelandetjänsttillägg {#notification-service-extension}

**För iOS**

Mediet måste hämtas på meddelanditjänstens tilläggsnivå.

```
#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage
```

## Meddelandeinnehållstillägg {#notification-content-extension}

**För iOS**

På den här nivån måste du:

* Koppla ditt innehållstillägg till kategorin som skickats av Adobe Campaign:

   Om du vill att mobilprogrammet ska visa en bild kan du ange kategorivärdet som &quot;image&quot; i Adobe Campaign och i mobilprogrammet skapar du ett meddelandetillägg med parametern **UNNotificationExtensionCategory** inställd på &quot;image&quot;. När push-meddelandet tas emot på enheten anropas tillägget enligt det definierade kategorivärdet.

* Definiera meddelandelayouten

   Du måste definiera en layout med relevanta widgetar. För en bild heter widgeten **UImageView**.

* Visa dina mediefiler

   Du måste lägga till kod för att mata in mediedata i widgeten. Här är ett exempel på kod för en bild:

   ```
   #import "NotificationViewController.h"
   #import <UserNotifications/UserNotifications.h>
   #import <UserNotificationsUI/UserNotificationsUI.h>
   
   @interface NotificationViewController () <UNNotificationContentExtension>
   
   @property (strong, nonatomic) IBOutlet UIImageView *imageView;
   @property (strong, nonatomic) IBOutlet UILabel *notifContent;
   @property (strong, nonatomic) IBOutlet UILabel *label;
   
   @end
   
   @implementation NotificationViewController
   
   - (void)viewDidLoad {
       [super viewDidLoad];
       // Do any required interface initialization here.
   }
   
   - (void)didReceiveNotification:(UNNotification *)notification {
       self.label.text = notification.request.content.title;
       self.notifContent.text = notification.request.content.body;
       UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
       if ([attachment.URL startAccessingSecurityScopedResource])
       {
         NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
         self.imageView.image =[UIImage imageWithData: imageData];
         [attachment.URL stopAccessingSecurityScopedResource];
       }
   }
   @end
   ```
