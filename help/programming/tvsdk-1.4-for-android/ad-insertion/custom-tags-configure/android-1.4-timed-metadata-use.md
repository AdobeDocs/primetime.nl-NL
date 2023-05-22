---
description: U kunt TimedMetadata gebruiken wanneer de huidige playbacktijd de begintijd aanpast.
title: Metagegevens met tijdslimiet gebruiken
exl-id: 7f87cd14-121a-4543-ab0a-a03d829d040b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Metagegevens met tijdslimiet gebruiken {#use-timed-metadata}

U kunt TimedMetadata gebruiken wanneer de huidige playbacktijd de begintijd aanpast.

Deze opgeslagen `TimedMetadata` objecten tijdens afspelen gebruiken de opgeslagen `ArrayList` van [Objecten met metagegevens met tijdinstellingen opslaan terwijl ze worden verzonden](../../ad-insertion/custom-tags-configure/android-1.4-timed-metadata-store.md).

1. Voer een timer uit en vul herhaaldelijk een query uit op de huidige afspeeltijd.
1. Alles zoeken `TimedMetadata` objecten met begintijden die overeenkomen met de huidige afspeeltijd.

   U kunt deze objecten gebruiken om verschillende handelingen uit te voeren.

   >[!IMPORTANT]
   >
   >Wanneer u controleert of de huidige afspeeltijd overeenkomt met een `TimedMetadata` objecten opnemen `shouldTriggerSubscribedTagEvent` als voorwaarde.

   De tijdlijn kan veranderen als gevolg van verschillende vormen van advertentie. Een of meer afbrekingen van een advertentie kunnen bijvoorbeeld vanaf de oorspronkelijke positie op de tijdlijn worden verplaatst, maar `shouldTriggerSubscribedTagEvent` ervoor zorgt dat de `TimeMetadata` de begintijd van het object komt overeen met de huidige afspeeltijd.

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

1. Periodiek uitspoelen `TimedMetadata` exemplaren van de lijst om te voorkomen dat het geheugen voortdurend toeneemt.
