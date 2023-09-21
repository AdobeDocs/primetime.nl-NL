---
description: De status van de mediaspeler bepaalt welke handelingen legaal zijn.
title: Levenscyclus en status van het MediaPlayer-object
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Levenscyclus en status van het MediaPlayer-object {#lifecycle-and-statuses-of-the-mediaplayer-object}

De status van de mediaspeler bepaalt welke handelingen legaal zijn.

Voor het werken met de status van de mediaspeler:

* U kunt de huidige status van het dialoogvenster `MediaPlayer` object met `MediaPlayer.getStatus()`.

* De lijst met statussen wordt gedefinieerd in het dialoogvenster [MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/com/adobe/mediacore/MediaPlayerStatus.html) enum.

Status-overgangsdiagram voor de levenscyclus van een `MediaPlayer` -instantie:
<!--<a id="fig_A6425F24C7734DC681D992859D2A6743"></a>-->

![](assets/media_player_statuses.png)

In de volgende tabel vindt u informatie over de levenscyclus en status van de mediaspeler:

<table id="table_82757A0043EB4AACA474E6B30326A6B7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Status </th> 
   <th colname="col2" class="entry"> Vindt plaats wanneer </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> IDLE </td> 
   <td colname="col2"> <p>De beginstatus van de mediaspeler. De speler wordt gemaakt en wacht tot u een mediaspeler-item opgeeft. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALISEREN </td> 
   <td colname="col2"> <p>Uw toepassingsvraag <span class="codeph"> MediaPlayer.replaceCurrentItem() </span>. </p> <p>Het item van de mediaspeler wordt geladen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> GEÏNITIALISEERD </td> 
   <td colname="col2"> <p>TVSDK heeft het media-player-item ingesteld. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VOORBEREIDEN </td> 
   <td colname="col2"> <p>Uw toepassingsvraag <span class="codeph"> MediaPlayer.prepareToPlay() </span>. De mediaspeler laadt het mediaspelitem en alle bijbehorende bronnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> BEREID </td> 
   <td colname="col2"> <p>TVSDK heeft de mediastream voorbereid en heeft geprobeerd de mediastream uit te voeren, op te lossen en in te voegen (indien ingeschakeld). De inhoud wordt voorbereid en de advertenties zijn ingevoegd in de tijdlijn of de advertentieprocedure is mislukt. </p> <p>Het bufferen of afspelen kan beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AFSPELEN/GEPAUZEERD </td> 
   <td colname="col2"> <p>Wanneer de toepassing de media afspeelt en pauzeert, beweegt de mediaspeler tussen deze statussen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> GESCHORST </td> 
   <td colname="col2"> <p>Als de toepassing niet bij het afspelen navigeert, het apparaat uitschakelt of tijdens het afspelen of pauzeren van de speler overschakelt, wordt de mediaspeler onderbroken en worden de bronnen vrijgegeven. </p> <p>Aanroepen <span class="codeph"> MediaPlayer.restore() </span> Geeft de speler terug naar de status waarin de speler zich bevond voordat deze werd GESUSPENDED. De uitzondering hierop is dat de speler ZOEKT wanneer de blokkering wordt aangeroepen, de speler wordt gepauzeerd en vervolgens SUSPENDED. </p> <p>Belangrijk:  <p>De volgende informatie onthouden: 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C">De <span class="codeph"> MediaPlayer </span> automatisch aanroepen <span class="codeph"> opschorten </span> alleen wanneer het oppervlakobject dat wordt gebruikt door de <span class="codeph"> MediaPlayerView </span> wordt vernietigd. </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1">De <span class="codeph"> MediaPlayer </span> automatisch aanroepen <span class="codeph"> restore() </span> alleen wanneer een nieuw object surface wordt gebruikt door de <span class="codeph"> MediaPlayerView </span> wordt gemaakt. </li> 
      </ul> </p> </p> <p>Als u altijd wilt dat het afspelen wordt gepauzeerd wanneer de MediaPlayer wordt teruggezet, moet u de aanroep van de toepassing uitvoeren <span class="codeph"> MediaPlayer.pause() </span> in de Android-activiteiten <span class="codeph"> onPause() </span> methode. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VOLTOOID </td> 
   <td colname="col2"> <p>De speler heeft het einde van de stream bereikt en het afspelen is gestopt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> UITGESCHAKELD </td> 
   <td colname="col2"> <p>Uw toepassing heeft de mediaspeler uitgebracht, die ook alle bijbehorende bronnen vrijgeeft. U kunt dit exemplaar niet meer gebruiken. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> FOUT </td> 
   <td colname="col2"> <p>Er is een fout opgetreden tijdens het proces. Een fout kan ook invloed hebben op wat de toepassing daarna kan doen. Zie voor meer informatie <a href="../../../tvsdk-2.7-for-android/content-playback-options/t-psdk-android-2.7-error-handling-set-up.md#set-up-error-handling" format="dita" scope="local"> Foutafhandeling instellen </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>U kunt de status gebruiken om feedback te geven over het proces, bijvoorbeeld een spinner in afwachting van de volgende statuswijziging, of de volgende stappen in het afspelen van de media uitvoeren, zoals wachten op de juiste status voordat u de volgende methode aanroept.

Bijvoorbeeld:

```java
mediaPlayer.addEventListener(MediaPlayerEvent STATUS_CHANGED, new StatusChangeEventListener() { 
    @Override  
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        switch(event.getStatus()) { 
            case INITIALIZED: 
                mediaPlayer.prepareToPlay(); 
                break; 
            case PREPARING: 
                showBufferingSpinner(); 
                break; 
            case PREPARED: 
                hideBufferingSpinner(); 
                mediaPlayer.play(); 
                break; 
            ...                
        } 
        ... 
    } 
}); 
```
