---
description: Vanaf het moment dat u de instantie MediaPlayer maakt tot het moment waarop u deze beëindigt (hergebruikt of verwijdert), voltooit deze instantie een reeks overgangen tussen frames.
title: Levenscyclus van MediaPlayer-objecten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Levenscyclus van MediaPlayer-objecten{#mediaplayer-object-lifecycle}

Vanaf het moment dat u de instantie MediaPlayer maakt tot het moment waarop u deze beëindigt (hergebruikt of verwijdert), voltooit deze instantie een reeks overgangen tussen frames.

Sommige bewerkingen zijn alleen toegestaan wanneer de speler zich in een bepaalde toestand bevindt. Bijvoorbeeld, roepen `play` in `IDLE` is niet toegestaan. U kunt deze status alleen aanroepen nadat de speler de `PREPARED` status.

Werken met frames:

* U kunt de huidige status van het dialoogvenster `MediaPlayer` object met `MediaPlayer.getStatus`.

  ```java
  PlayerState getStatus() throws IllegalStateException;
  ```

* De lijst met staten wordt gedefinieerd in `MediaPlayer.PlayerState`.

Overgangsdiagram voor de levenscyclus van een `MediaPlayer` -instantie:
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

De volgende tabel bevat aanvullende gegevens:

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> MediaPlayer.PlayerState </th> 
   <th colname="col2" class="entry"> Vindt plaats wanneer </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> IDLE </span> </td> 
   <td colname="col2"> <p>Uw toepassing heeft een nieuwe mediaspeler aangevraagd door <span class="codeph"> DefaultMediaPlayer.create </span>. De nieuwe speler wacht op het opgeven van een mediaspeler-item. Dit is de begintoestand van de mediaspeler. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALISEREN </span> </td> 
   <td colname="col2"> <p>Uw toepassing is opgeroepen <span class="codeph"> MediaPlayer.replaceCurrentItem </span>en de mediaspeler wordt geladen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> GEÏNITIALISEERD </span> </td> 
   <td colname="col2"> <p>TVSDK heeft het mediaspeleritem ingesteld. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> VOORBEREIDEN </span> </td> 
   <td colname="col2"> <p>Uw toepassing is opgeroepen <span class="codeph"> MediaPlayer.prepareToPlay </span>. De mediaspeler laadt het mediaspelitem en de bijbehorende bronnen. </p> <p>Tip: er kan zich een buffering van de hoofdmedia voordoen. </p> <p>TVSDK bereidt de mediastream voor en probeert (indien ingeschakeld) het invoegen en oplossen van advertenties uit te voeren. </p> <p>Tip: als u de begintijd op een andere waarde dan nul wilt instellen, roept u <span class="codeph"> prepareToPlay(startTime) </span> in milliseconden. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> BEREID </span> </td> 
   <td colname="col2"> <p>De inhoud wordt voorbereid en de advertenties zijn ingevoegd in de tijdlijn of de advertentieprocedure is mislukt. Het bufferen of afspelen kan beginnen. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AFSPELEN </span> </td> 
   <td colname="col2"> <p>Uw toepassing heeft <span class="codeph"> play </span>, dus probeert TVSDK de video af te spelen. Er kan sprake zijn van buffering voordat de video daadwerkelijk wordt afgespeeld. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> GEPAUZEERD </span> </td> 
   <td colname="col2"> <p>Wanneer de media in de toepassing worden afgespeeld en gepauzeerd, verplaatst de mediaspeler zich tussen deze status en PLAYING. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> GESCHORST </span> </td> 
   <td colname="col2"> <p>De toepassing navigeerde weg van het afspelen, sloot het apparaat of geschakelde toepassingen terwijl de speler werd afgespeeld of gepauzeerd. De mediaspeler is opgeschort en er zijn bronnen vrijgemaakt. Herstel de mediaspeler om door te gaan. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> VOLTOOID </span> </td> 
   <td colname="col2"> <p>De speler heeft het einde van de stream bereikt en het afspelen is gestopt. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> UITGESCHAKELD </span> </td> 
   <td colname="col2"> <p>Uw toepassing heeft de mediaspeler uitgebracht, die ook alle bijbehorende bronnen vrijgeeft. U kunt deze instantie niet meer gebruiken </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> FOUT </span> </td> 
   <td colname="col2"> <p>Er is een fout opgetreden tijdens het proces. Een fout kan ook van invloed zijn op wat de toepassing daarna kan doen. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>U kunt de status gebruiken om feedback te geven over het proces (bijvoorbeeld een spinner in afwachting van de volgende statuswijziging) of om de volgende stap uit te voeren bij het afspelen van de media, bijvoorbeeld wachten op de juiste status voordat u de volgende methode aanroept.

Bijvoorbeeld:

```java
@Override 
public void onStateChanged(MediaPlayer.PlayerState state,  
                           MediaPlayerNotification notification) { 
   switch (state) { 
      // It is recommended that you call prepareToPlay() after receiving  
      // the INITIALIZED state. 
      case INITIALIZED: 
         _mediaPlayer.prepareToPlay(); 
         break; 
      case PREPARING: 
         showBufferingSpinner(); 
         break; 
      case PREPARED: 
         hideBufferingSpinner(); 
      ..... 
    } 
}
```
