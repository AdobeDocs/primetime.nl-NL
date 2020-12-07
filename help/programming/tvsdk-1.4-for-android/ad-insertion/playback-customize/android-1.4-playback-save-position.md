---
description: U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.
seo-description: U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.
seo-title: De videopositie opslaan en later hervatten
title: De videopositie opslaan en later hervatten
uuid: 322f780d-09ba-44b0-b2e5-46288bf58fda
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---


# De videopositie opslaan en later {#save-the-video-position-and-resume-later} hervatten

U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.

Dynamisch ingevoegde advertenties verschillen per gebruikerssessie, zodat het opslaan van de positie **met** gespliceerde advertenties naar een andere positie in een toekomstige sessie verwijst. TVSDK biedt methoden om de afspeelpositie op te halen zonder gespliceerde advertenties te negeren.

1. Wanneer de gebruiker een video afsluit, wordt de positie in de video opgehaald en opgeslagen.

   >[!TIP]
   >
   >Duur van advertentie is niet inbegrepen.

   De pauzes van de toevoeging kunnen in elke zitting als toe te schrijven aan advertentiepatronen, frequentiegrenzen, etc. variëren. De huidige tijd van de video in één sessie kan in een volgende sessie anders zijn. Wanneer u een positie in de video opslaat, haalt de toepassing de lokale tijd op, die u op het apparaat of in een database op de server kunt opslaan.

   Als de gebruiker bijvoorbeeld op de 20e minuut van de video staat en deze positie vijf minuten aan advertenties bevat, retourneert `getCurrentTime` 1200 seconden, terwijl `getLocalTime` op deze positie 900 seconden retourneert.

   >[!IMPORTANT]
   >
   >De lokale tijd en de huidige tijd zijn het zelfde voor levende/lineaire stromen. In dit geval heeft `convertToLocalTime` geen effect. Voor VOD blijft de lokale tijd ongewijzigd tijdens het afspelen van advertenties.

   ```java
   // Save the user session when player activity stops 
   @Override 
   public void onStop() { 
       super.onStop(); 
       ... 
       prefs = PreferenceManager.getDefaultSharedPreferences( 
                 getActivity().getApplicationContext() 
               ); 
       SharedPreferences.Editor editor = prefs.edit(); 
       // get the local time where stream stopped playing and  
       // save it in System preferences 
       editor.putLong(LAST_LOCAL_TIME, _mediaPlayer.getLocalTime());  
       editor.putString(LAST_MEDIA_RESOURCE, _contentInfo.toMediaResource().getUrl()); 
       editor.commit(); 
       ... 
   } 
   ```

1. Herstel de gebruikerssessie wanneer de activiteit van de speler wordt hervat.

   ```java
   @Override 
   public void onResume() { 
       super.onResume(); 
       ... 
       prefs = PreferenceManager.getDefaultSharedPreferences(getActivity().getApplicationContext()); 
       if (prefs.getString(LAST_MEDIA_RESOURCE, "nil").equals(_contentInfo.toMediaResource().getUrl())) { 
   
           _lastKnownLocalTime = prefs.getLong(LAST_LOCAL_TIME, 0);    // get the last local time saved  
                                                                       // in system preferences 
           if (_lastKnownLocalTime > 0) { 
               _shouldResumePlayback = true; 
           } 
       } 
       ... 
   } 
   ```

1. De video op dezelfde positie hervatten:

   * Gebruik `seekToLocalTime` om het afspelen van de video vanaf de positie die is opgeslagen tijdens een vorige sessie te hervatten.

      >[!TIP]
      >
      >Deze methode wordt alleen aangeroepen met lokale tijdwaarden. Als de methode wordt aangeroepen met de huidige-tijdresultaten, treedt een onjuist gedrag op.

   * Gebruik `seek` om naar de huidige tijd te zoeken.

1. Wanneer uw toepassing de gebeurtenis `onStatusChanged` van de statusverandering ontvangt, zoek aan de bewaarde lokale tijd.

   ```java
   private final MediaPlayer.PlaybackEventListener _playbackEventListener =  
     new MediaPlayer.PlaybackEventListener() { 
       @Override 
       public void onPrepared() { 
           ... 
           if (_shouldResumePlayback) { 
               if(_lastKnownLocalTime >= 0) { 
                   _mediaPlayer.seekToLocalTime(_lastKnownLocalTime); 
               } 
           } 
           ... 
       } 
        ... 
   } 
   ```

1. Geef de pagina-einden op zoals opgegeven in de interface voor advertentiebeleid.
1. Voer een douaneselecteur van het advertentiebeleid uit door de standaard uit te breiden en beleidsselecteur.
1. Geef de ad-einden op die aan de gebruiker moeten worden weergegeven door `selectAdBreaksToPlay` te implementeren.

   Deze methode omvat een pre-rol en onderbreking en de middenrol en pauzes vóór de lokale tijdpositie. Uw toepassing kan besluiten een pre-rol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, een middenrol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, of geen ad onderbrekingen te spelen.
