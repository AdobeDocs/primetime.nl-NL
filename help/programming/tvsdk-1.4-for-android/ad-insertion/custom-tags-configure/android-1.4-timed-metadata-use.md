---
description: U kunt TimedMetadata gebruiken wanneer de huidige playbacktijd de begintijd aanpast.
seo-description: U kunt TimedMetadata gebruiken wanneer de huidige playbacktijd de begintijd aanpast.
seo-title: Metagegevens met tijdslimiet gebruiken
title: Metagegevens met tijdslimiet gebruiken
uuid: 98bb8c08-2794-42d6-b5c3-b1047ac804fe
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---


# Metagegevens met tijdslimiet gebruiken {#use-timed-metadata}

U kunt TimedMetadata gebruiken wanneer de huidige playbacktijd de begintijd aanpast.

Als u deze opgeslagen `TimedMetadata`-objecten tijdens het afspelen wilt gebruiken, gebruikt u de opgeslagen `ArrayList` van [Objecten met getimede metagegevens opslaan wanneer ze worden verzonden](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md).

1. Voer een timer uit en vul herhaaldelijk een query uit op de huidige afspeeltijd.
1. Alle `TimedMetadata`-objecten zoeken met begintijden die overeenkomen met de huidige afspeeltijd.

   U kunt deze objecten gebruiken om verschillende handelingen uit te voeren.

   >[!IMPORTANT]
   >
   >Wanneer u controleert of de huidige afspeeltijd overeenkomt met een `TimedMetadata`-object, neemt u `shouldTriggerSubscribedTagEvent` op als voorwaarde.

   De tijdlijn kan veranderen als gevolg van verschillende vormen van advertentie. Een of meer afbrekingen van een advertentie kunnen bijvoorbeeld vanaf de oorspronkelijke positie op de tijdlijn worden verplaatst, maar `shouldTriggerSubscribedTagEvent` zorgt ervoor dat de begintijd van het object `TimeMetadata` overeenkomt met de huidige afspeeltijd.

   Bijvoorbeeld:

   ```java
    _playbackClockEventListener = new Clock.ClockEventListener() {
       @Override
       public void onTick(String name) {
           getActivity().runOnUiThread(new Runnable() {
               @Override
               public void run() {
                   /* handle timedmetadata object list  */ 
                   if (_mediaPlayer != null && _timedMetadataList != null && _timedMetadataList.size() > 0) {
                       if (_lastKnownStatus == MediaPlayer.PlayerState.PLAYING) {
                           long localTime = _mediaPlayer.getLocalTime();
                           Iterator<TimedMetadata> iterator = _timedMetadataList.iterator(); 
                           while (iterator.hasNext()) {
                               TimedMetadata timedMetadata = iterator.next();
                               long diff = localTime - timedMetadata.getTime();
                               if (diff >= 0 &&
                                   diff <= PLAYBACK_CLOCK_INTERVAL &&
                                   _mediaPlayer.shouldTriggerSubscribedTagEvent()) {
                                   // use timed metadata object
                               }
                           }
                       }
                   }
               }
           });
       }
   };
   _playbackClock.addClockEventListener(_playbackClockEventListener);
   ```

1. Verwijder regelmatig `TimedMetadata` exemplaren van de lijst om te voorkomen dat het geheugen voortdurend toeneemt.