---
description: De TVSDK MediaPlayer onderbreken en herstellen wanneer een apparaatscherm wordt uitgeschakeld en ingeschakeld, moet door de toepassing worden afgehandeld.
keywords: SurfaceView;Suspend;Restore;BroadcastReceiver
seo-description: De TVSDK MediaPlayer onderbreken en herstellen wanneer een apparaatscherm wordt uitgeschakeld en ingeschakeld, moet door de toepassing worden afgehandeld.
seo-title: MediaPlayer onderbreken en herstellen
title: MediaPlayer onderbreken en herstellen
uuid: 624a87df-df65-4358-915b-c09a3a4fa224
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# MediaPlayer onderbreken en herstellen {#suspend-and-restore-mediaplayer}

De TVSDK MediaPlayer onderbreken en herstellen wanneer een apparaatscherm wordt uitgeschakeld en ingeschakeld, moet door de toepassing worden afgehandeld.

U kunt de bewerkingen op de ontvanger van de Android-uitzending onderbreken en herstellen voor het in- en uitschakelen van het scherm. `MediaPlayer`

TVSDK kan niet bepalen wanneer een fragment (of activiteit) zich op de achtergrond of voorgrond bevindt. Bovendien wordt Android `SurfaceView` niet vernietigd wanneer het apparaatscherm wordt uitgeschakeld (maar de activiteit wordt gepauzeerd). De toepassing wordt echter `SurfaceView`*wel* vernietigd wanneer het apparaat de toepassing op de achtergrond plaatst. TVSDK kan geen van deze wijzigingen detecteren, dus deze moeten door uw toepassing worden verwerkt.

In het volgende voorbeeld ziet u hoe uw toepassing het opschorten en herstellen van het apparaat kan afhandelen `MediaPlayer` wanneer het apparaatscherm op toepassingsniveau wordt in- en uitgeschakeld:

```java
// Track the state of a fragment to determine if it is PAUSED or RESUMED 
private boolean isActivityPaused = false; 
 
/** 
* Register the broadcast receiver to track screen on/screen off functions triggered from 
device. 
*/ 
private BroadcastReceiver mReceiver = new BroadcastReceiver() { 
    @Override 
    public void onReceive(Context context, Intent intent) { 
 
        // Call suspend when screen is turned off and mediaPlayer is not null and 
        // mediaplayer status is not suspended/Error/Released state. 
        if (intent.getAction().equals(Intent.ACTION_SCREEN_OFF)) { 
            try { 
                if (mediaPlayer != null && 
                  lastKnownStatus != MediaPlayerStatus.ERROR && 
                  lastKnownStatus != MediaPlayerStatus.RELEASED && 
                  lastKnownStatus != MediaPlayerStatus.SUSPENDED) { 
                    PrimetimeReference.logger.i(LOG_TAG+"#screenOff:", 
                    "Suspending mediaplayer as screen is turned off and mediaPlayer 
                    status is " + lastKnownStatus.toString()); 
                    mediaPlayer.suspend(); 
                } 
                else { 
                    PrimetimeReference.logger.i(LOG_TAG+"#screenOff:", 
                      "Not suspending mediaplayer since mediaplayer status is " 
                      + lastKnownStatus.toString()); 
                } 
            } catch(MediaPlayerException e) { 
                PrimetimeReference.logger.e(LOG_TAG+"#screenOff:", 
                  "MediaPlayer Exception for suspend() call"); 
            } 
        } 
        else if (intent.getAction().equals(Intent.ACTION_SCREEN_ON)) { 
            // Call restore when the screen is turned on and mediaplayer is not in the  
            // suspended status.  This is for the screen on condition when the device  
            // does not have a lock and turning on the screen immediately brings the  
            // fragment to the foreground. 
            try { 
                if(lastKnownStatus == MediaPlayerStatus.SUSPENDED && !isActivityPaused) { 
                    PrimetimeReference.logger.i(LOG_TAG+"#screenOn:", 
                      "Restoring mediaplayer since screen is turned on and mediaPlayer status is " 
                      + lastKnownStatus.toString()); 
                    mediaPlayer.restore(); 
                } 
                else { 
                    PrimetimeReference.logger.i(LOG_TAG+"#screenOn:", 
                      "Not restoring mediaplayer since mediaPlayer status is " 
                      + lastKnownStatus.toString()); 
                } 
            } catch(MediaPlayerException e) { 
                PrimetimeReference.logger.e(LOG_TAG+"#screenOn:", 
                  "MediaPlayer Exception for restore() call"); 
            } 
        } 
    } 
}; 
 
/* 
* Activity or Fragment's onPause() overridden method 
*/ 
@Override 
public void onPause() { 
    PrimetimeReference.logger.i(LOG_TAG + "#onPause", "Player activity paused."); 
 
    // Set the fragment paused status to true when app goes in background. 
    isActivityPaused = true; 
    super.onPause(); 
} 
 
/* 
* Activity or Fragment's onResume() overridden method 
*/ 
@Override 
public void onResume() { 
    super.onResume(); 
 
    /** 
    * When the device has a lock/pin the on resume will be called only after the device 
      is unlocked. 
    * Screen on does not call the onResume() method so we need to handle restore here 
      explicitly. 
    */ 
    if(lastKnownStatus == MediaPlayerStatus.SUSPENDED && isActivityPaused) { 
        try { 
            PrimetimeReference.logger.i(LOG_TAG + "#onResume", 
              "Player restored as activity operations are resumed"); 
            mediaPlayer.restore(); 
        } 
        catch(MediaPlayerException e) { 
            PrimetimeReference.logger.i(LOG_TAG + "#onResume",  
              "Exception occured while restoring mediaPlayer"); 
        } 
    } 
    // Set the fragment paused status to false when app comes in foreground. 
    isActivityPaused = false; 
} 
```
