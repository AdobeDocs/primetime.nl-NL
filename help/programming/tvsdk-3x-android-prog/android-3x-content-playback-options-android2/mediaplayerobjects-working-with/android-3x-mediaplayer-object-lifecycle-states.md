---
description: De status van de mediaspeler bepaalt welke handelingen legaal zijn.
seo-description: De status van de mediaspeler bepaalt welke handelingen legaal zijn.
seo-title: Levenscyclus en status van het MediaPlayer-object
title: Levenscyclus en status van het MediaPlayer-object
uuid: a2866f84-a722-46ed-b4cb-36664db5be82
translation-type: tm+mt
source-git-commit: 56dc79e5b4df11ff730d7d8f23dea8d0f4712077
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Levenscyclus en status van het MediaPlayer-object{#lifecycle-and-statuses-of-the-mediaplayer-object}

De status van de mediaspeler bepaalt welke handelingen legaal zijn.

Voor het werken met de status van de mediaspeler:

* U kunt de huidige status van het object `MediaPlayer` ophalen met `MediaPlayer.getStatus()`.

* De lijst met statussen wordt gedefinieerd in de opsomming [MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/com/adobe/mediacore/MediaPlayerStatus.html).

Status-overgangsdiagram voor de levenscyclus van een `MediaPlayer` instantie:

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
   <td colname="col2"> <p>Uw toepassing roept <span class="codeph"> MediaPlayer.replaceCurrentItem() </span>. </p> <p>Het item van de mediaspeler wordt geladen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> GEÏNITIALISEERD </td> 
   <td colname="col2"> <p>TVSDK heeft het media-player-item ingesteld. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> VOORBEREIDEN </td> 
   <td colname="col2"> <p>Uw toepassing roept <span class="codeph"> MediaPlayer.prepareToPlay() </span> aan. De mediaspeler laadt het mediaspelitem en alle bijbehorende bronnen. </p> </td> 
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
   <td colname="col2"> <p>Als de toepassing niet bij het afspelen navigeert, het apparaat uitschakelt of tijdens het afspelen of pauzeren van de speler overschakelt, wordt de mediaspeler onderbroken en worden de bronnen vrijgegeven. </p> <p>Wanneer <span class="codeph"> MediaPlayer.restore() </span> wordt aangeroepen, wordt de speler teruggezet naar de status waarin deze zich bevond voordat deze werd GESUSPENDED. De uitzondering hierop is dat de speler ZOEKT wanneer de blokkering wordt aangeroepen, de speler wordt gepauzeerd en vervolgens SUSPENDED. </p> <p>Belangrijk:  <p>De volgende informatie onthouden: 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C">De <span class="codeph"> MediaPlayer </span> roept <span class="codeph"> automatisch </span> op wanneer het oppervlakvoorwerp dat door <span class="codeph"> MediaPlayerView </span> wordt gebruikt wordt vernietigd. </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1">De <span class="codeph"> MediaPlayer </span> roept <span class="codeph"> restore() </span> alleen automatisch aan wanneer een nieuw oppervlakobject wordt gemaakt dat door de <span class="codeph"> MediaPlayerView </span> wordt gebruikt. </li> 
      </ul> </p> </p> <p>Als u het afspelen altijd wilt pauzeren wanneer de MediaPlayer wordt teruggezet, moet u de toepassingsaanroep <span class="codeph"> MediaPlayer.pause() </span> in de Android Activity's <span class="codeph"> onPause() </span>-methode plaatsen. </p> </td> 
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
   <td colname="col2"> <p>Er is een fout opgetreden tijdens het proces. Een fout kan ook invloed hebben op wat de toepassing daarna kan doen. Zie <a href="../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-error-handling-set-up.md" format="dita" scope="local"> Foutafhandeling instellen </a> voor meer informatie. </p> </td> 
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
