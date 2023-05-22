---
description: U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.
title: De videopositie opslaan en later hervatten
exl-id: cf7111c1-7d9c-4f35-ac3d-d02c69c1524c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# De videopositie opslaan en later hervatten {#save-the-video-position-and-resume-later}

U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.

Dynamisch ingevoegde advertenties verschillen per gebruikerssessie, zodat de positie wordt opgeslagen **with** spliced advertenties verwijzen naar een andere positie in een toekomstige sessie. TVSDK biedt methoden om de afspeelpositie op te halen zonder gespliceerde advertenties te negeren.

1. Wanneer de gebruiker een video afsluit, wordt de positie in de video opgehaald en opgeslagen.

   >[!TIP]
   >
   >Duur van advertentie is niet inbegrepen.

   De pauzes van de toevoeging kunnen in elke zitting als toe te schrijven aan advertentiepatronen, frequentiegrenzen, etc. variëren. De huidige tijd van de video in één sessie kan in een volgende sessie anders zijn. Wanneer u een positie in de video opslaat, haalt de toepassing de lokale tijd op, die u op het apparaat of in een database op de server kunt opslaan.

   Als de gebruiker bijvoorbeeld op de twintigste minuut van de video staat en deze positie vijf minuten aan advertenties bevat, `getCurrentTime` zal 1200 seconden terugkeren, terwijl `getLocalTime` op deze positie wordt 900 seconden geretourneerd.

   >[!IMPORTANT]
   >
   >De lokale tijd en de huidige tijd zijn het zelfde voor levende/lineaire stromen. In dit geval: `convertToLocalTime` heeft geen effect. Voor VOD blijft de lokale tijd ongewijzigd tijdens het afspelen van advertenties.

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

   * Als u het afspelen van de video wilt hervatten vanaf de positie die u tijdens een vorige sessie hebt opgeslagen, gebruikt u `seekToLocalTime`.

      >[!TIP]
      >
      >Deze methode wordt alleen aangeroepen met lokale tijdwaarden. Als de methode wordt aangeroepen met de huidige-tijdresultaten, treedt een onjuist gedrag op.

   * Om naar de huidige tijd te zoeken, gebruik `seek`.

1. Wanneer uw toepassing de `onStatusChanged` wijzigt de status, zoekt naar de opgeslagen lokale tijd.

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
1. Geef de ad-einden op die aan de gebruiker moeten worden weergegeven door de implementatie `selectAdBreaksToPlay`.

   Deze methode omvat een pre-rol en onderbreking en de middenrol en pauzes vóór de lokale tijdpositie. Uw toepassing kan besluiten een pre-rol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, een middenrol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, of geen ad onderbrekingen te spelen.
