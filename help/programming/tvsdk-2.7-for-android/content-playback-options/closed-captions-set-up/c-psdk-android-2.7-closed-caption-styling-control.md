---
description: U kunt opmaakinformatie opgeven voor Closed Caption-tracks met behulp van de klasse TextFormat, die de stijl instelt voor Closed Captions die door de speler worden weergegeven.
seo-description: U kunt opmaakinformatie opgeven voor Closed Caption-tracks met behulp van de klasse TextFormat, die de stijl instelt voor Closed Captions die door de speler worden weergegeven.
seo-title: Opmaak van ondertiteling beheren
title: Opmaak van ondertiteling beheren
uuid: fa4f637f-f13c-465d-8eee-5e66a6dd9db2
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 0%

---


# Opmaak van ondertiteling beheren {#control-closed-caption-styling}

U kunt opmaakinformatie opgeven voor Closed Caption-tracks met behulp van de klasse TextFormat, die de stijl instelt voor Closed Captions die door de speler worden weergegeven.

Met deze klasse worden opmaakgegevens voor gesloten bijschriften ingekapseld, zoals het lettertype, de grootte, de kleur en de achtergronddekking.

## Stijlen voor een gesloten bijschrift instellen {#section_C9B5E75C70DD42E59DC4DD0F308C8216}

U kunt de tekst met een gesloten bijschrift opmaken met de methoden TVSDK.

1. Wacht tot de mediaspeler ten minste de `PREPARED` status heeft.
1. Maak een `TextFormatBuilder` instantie.

   U kunt nu alle opmaakparameters voor een gesloten bijschrift opgeven of deze later instellen.

   TVSDK kapselt uit een gesloten bijschrift opmaakgegevens in de `TextFormat` interface in. De `TextFormatBuilder` klasse maakt objecten die deze interface implementeren.

   ```java
   public TextFormatBuilder( 
      TextFormat.Font font, 
      TextFormat.Size size, 
      TextFormat.FontEdge fontEdge, 
      java.lang.String fontColor, 
      java.lang.String backgroundColor, 
      java.lang.String fillColor, 
      java.lang.String edgeColor, 
      int fontOpacity, 
      int backgroundOpacity, 
      int fillOpacity 
      java.lang.String bottomInset, 
      java.lang.String safeArea)
   ```

1. Om een verwijzing naar een voorwerp te verkrijgen dat de `TextFormat` interface uitvoert, roep de `TextFormatBuilder.toTextFormat` openbare methode.

   >[!NOTE]
   >
   >Hiermee wordt een `TextFormat` object geretourneerd dat op de mediaspeler kan worden toegepast.

   ```java
   public TextFormat toTextFormat()
   ```

1. U kunt desgewenst de huidige stijlinstellingen voor een gesloten bijschrift ophalen door een van de volgende handelingen uit te voeren:

   * Hiermee worden alle stijlinstellingen opgehaald met `MediaPlayer.getCCStyle` De geretourneerde waarde is een instantie van de `TextFormat` interface.

      ```java
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws MediaPlayerException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws MediaPlayerException;
      ```

   * Krijg de montages één voor één door de methodes van de `TextFormat` interfacetter.

      ```java
      public java.lang.String getFontColor(); 
      public java.lang.String getBackgroundColor(); 
      public java.lang.String getFillColor(); // retrieve the font fill color 
      public java.lang.String getEdgeColor(); // retrieve the font edge color 
      public TextFormat.Size getSize(); // retrieve the font size 
      public TextFormat.FontEdge getFontEdge(); // retrieve the font edge type 
      public TextFormat.Font getFont(); // retrieve the font type 
      public int getFontOpacity(); 
      public int getBackgroundOpacity(); 
      public java.lang.String getBottomInset(java.lang.String bi); 
      public java.lang.String getSafeArea(java.lang.String sa);
      ```

1. Voer een van de volgende handelingen uit om de stijlinstellingen te wijzigen:

   * Gebruik de methode setter `MediaPlayer.setCCStyle`en geef een instantie van de `TextFormat` interface door:

      ```java
      /** 
      * Sets the closed captioning style. Used to control the closed captioning font, 
      * size, color, edge and opacity.  
      * 
      * This method is safe to use even if the current media stream doesn't have closed 
      * captions. 
      * 
      * @param textFormat 
      * @throws MediaPlayerException 
      */ 
      public void setCCStyle(TextFormat textFormat) throws MediaPlayerException;
      ```

   * Gebruik de `TextFormatBuilder` klasse, die afzonderlijke settermethoden definieert.

      De `TextFormat` interface definieert een onveranderlijk object, zodat er alleen methoden getter en geen setters zijn. U kunt de opmaakparameters voor Closed Caption alleen instellen met de `TextFormatBuilder` klasse:

      ```java
      // set font type 
      public void setFont(Font font)  
      public void setBackgroundColor(String backgroundColor) 
      public void setFillColor(String fillColor) 
      // set the font-edge color 
      public void setEdgeColor(String edgeColor)  
      // set the font size 
      public void setSize(Size size)  
      // set the font edge type 
      public void setFontEdge(FontEdge fontEdge)  
      public void setFontOpacity(int fontOpacity) 
      public void setBackgroundOpacity(int backgroundOpacity) 
      // set the font-fill opacity level 
      public void setFillOpacity(int fillOpacity)  
      public void setFontColor(String fontColor) 
      public void setBottomInset(String bi) 
      public void setSafeArea(String sa) 
      public void setTreatSpaceAsAlphaNum(bool)
      ```

      >[!IMPORTANT]
      >
      >**Kleurinstellingen:** In Android TVSDK 2.X is de kleurstijl van gesloten bijschriften verbeterd. Dankzij deze verbetering kunt u Closed Caption-kleuren instellen met een hexadecimale tekenreeks die RGB-kleurwaarden vertegenwoordigt. De hexadecimale RGB-kleurrepresentatie is de bekende tekenreeks van 6 bytes die u gebruikt in toepassingen zoals Photoshop:
      >
      >    * FFFFFF = Zwart
      >    * 000000 = wit
      >    * FF0000 = rood
      >    * 00FF00 = Groen
      >    * 0000FF = blauw

      >
      >enzovoort.
      >
      >Wanneer u in uw toepassing informatie over kleurstijlen doorgeeft, gebruikt u de `TextFormatBuilder`opsomming nog steeds zoals voorheen, maar nu moet u de kleur toevoegen `Color` `getValue()` om de waarde als tekenreeks op te halen. Bijvoorbeeld:

      ```
      tfb = tfb.setBackgroundColor(TextFormat.Color.RED <b>.getValue()</b>);
      ```




Het instellen van de stijl voor een Closed Caption is een asynchrone bewerking. Het kan dus enkele seconden duren voordat de wijzigingen op het scherm worden weergegeven.

## Opties voor de stijl van gesloten bijschriften {#section_6D685EC2D58C42A2BDDD574EDFCCC2A0}

U kunt meerdere opties voor de bijschriftstijlen opgeven. Deze opties overschrijven de stijlopties in de originele bijschriften.

```java
public TextFormatBuilder( 
   Font font, 
   Size size, 
   FontEdge fontEdge, 
   String fontColor, 
   String backgroundColor, 
   String fillColor, 
   String edgeColor, 
   int fontOpacity, 
   int backgroundOpacity, 
   int fillOpacity,  
   String bottomInset 
   String safeArea)
```

>[!TIP]
In opties die standaardwaarden definiëren (bijvoorbeeld `DEFAULT`), verwijst die waarde naar de instelling op het moment dat het bijschrift oorspronkelijk werd opgegeven.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Indeling </th> 
   <th colname="2" class="entry"> Beschrijving </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Lettertype </td> 
   <td colname="2"> <p>Het lettertype. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de <span class="codeph"> </span> opsomming TextFormat.Font en die bijvoorbeeld een vaste spatiëring met of zonder schreef vertegenwoordigt. </p> <p>Tip:  De werkelijke lettertypen die op een apparaat beschikbaar zijn, kunnen variëren en waar nodig worden vervangende lettertypen gebruikt. Monospace met schreef wordt typisch gebruikt als substituut, hoewel deze substitutie systeemspecifiek kan zijn. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Grootte </td> 
   <td colname="2"> <p>De grootte van het bijschrift. </p> <p> Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de <span class="codeph"> opsomming TextFormat.Size </span> : 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> - De standaardgrootte </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROOT </span> - ongeveer 30% groter dan gemiddeld </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEINE </span> - ongeveer 30% kleiner dan gemiddeld </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDAARD </span> - De standaardgrootte voor het bijschrift; gelijk aan medium </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fontrand </td> 
   <td colname="2"> <p>Het effect dat voor de fontrand wordt gebruikt, zoals verhoogd of geen. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de <span class="codeph"> opsomming TextFormat.FontEdge </span> . </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fontkleur </td> 
   <td colname="2"> <p>De fontkleur. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de <span class="codeph"> </span> opsomming TextFormat.Color. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Randkleur </td> 
   <td colname="2"> <p>De kleur van het randeffect. </p> <p>Kan worden ingesteld op alle waarden die beschikbaar zijn voor de lettertypekleur. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Achtergrondkleur </td> 
   <td colname="2"> <p>De kleur van de achtergrondtekencel. </p> <p>Kan alleen worden ingesteld op waarden die beschikbaar zijn voor de lettertypekleur. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Vulkleur </td> 
   <td colname="2"> <p>De kleur van de achtergrond van het venster waarin de tekst zich bevindt. </p> <p>Kan worden ingesteld op alle waarden die beschikbaar zijn voor de lettertypekleur. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Dekking van lettertype </td> 
   <td colname="2"> <p>De dekking van de tekst. </p> <p>Uitgedrukt als een percentage tussen 0 (volledig transparant) en 100 (volledig dekkend). <span class="codeph"> DEFAULT_OPACITY </span> voor het lettertype is 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Achtergronddekking </td> 
   <td colname="2"> <p>De dekking van de cel van het achtergrondteken. </p> <p>Uitgedrukt als een percentage tussen 0 (volledig transparant) en 100 (volledig dekkend). <span class="codeph"> DEFAULT_OPACITY </span> voor de achtergrond is 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Vuldekking </td> 
   <td colname="2"> <p>De dekking van de achtergrond van het bijschriftvenster. </p> <p>Uitgedrukt als een percentage tussen 0 (volledig transparant) en 100 (volledig dekkend). <span class="codeph"> DEFAULT_OPACITY </span> voor vulling is 0. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Onderste inzet </td> 
   <td colname="2"> <p>De verticale afstand tussen de onderkant van het bijschriftvenster voor bijschriften moet worden vermeden. </p> <p>Wordt uitgedrukt als een percentage van de hoogte van het bijschriftvenster (bijvoorbeeld "20%") of een aantal pixels (bijvoorbeeld "20"). </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> Veilig gebied </td> 
   <td colname="2"> <p>Een gebied rond de rand van het scherm tussen 0% en 25% waar bijschriften niet worden weergegeven. </p> <p>Standaard is het veilige gebied voor WebVTT 0%. Met deze instelling kan uw toepassing deze standaardinstelling overschrijven. Wanneer twee waarden worden opgegeven, bijvoorbeeld de tekenreeks "10%,20%", is de eerste waarde het horizontale veilige gebied en de tweede waarde het verticale veilige gebied. Wanneer bijvoorbeeld één waarde wordt opgegeven, gebruikt de tekenreeks "15%", zowel de verticale als de horizontale as het opgegeven veilige gebied. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Voorbeelden van bijschriftopmaak {#section_58E8E82494EC4683B010FFDE67485CF9}

Hier volgen enkele voorbeelden waarin u kunt zien hoe u de opmaak van een gesloten bijschrift kunt opgeven.

**Voorbeeld 1: Opmaakwaarden expliciet opgeven**

```java
private final MediaPlayer.PlaybackEventListener _playbackEventListener = 
  new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // Set CC style. 
        TextFormat tf = new TextFormatBuilder( 
            TextFormat.Font.DEFAULT, 
            TextFormat.Size.DEFAULT, 
            TextFormat.FontEdge.DEFAULT, 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.DEFAULT_OPACITY, 
            TextFormat.DEFAULT_OPACITY, 
            TextFormat.DEFAULT_OPACITY).toTextFormat(); 
 
        mediaPlayer.setCCStyle(tf); 
        ... 
    } 
} 
```

**Voorbeeld 2: Opmaakwaarden opgeven in parameters**

```java
/** 
* Constructor using parameters to initialize a TextFormat. 
* 
* @param font 
* The desired font. 
* @param size 
* The desired text size. 
* @param fontEdge 
* The desired font edge. 
* @param fontColor 
* The desired font color. 
* @param backgroundColor 
* The desired background color. 
* @param fillColor 
* The desired fill color. 
* @param edgeColor 
* The desired color to draw the text edges. 
* @param fontOpacity  
* The desired font opacity. 
* @param backgroundOpacity 
* The desired background opacity. 
* @param fillOpacity 
* The desired fill opacity.  
*/ 
public  
<b>TextFormatBuilder</b>( 
    Font font, Size size, FontEdge fontEdge, 
    String fontColor, String backgroundColor,  
    String fillColor, String edgeColor, 
    int fontOpacity, int backgroundOpacity, 
    int fillOpacity); 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public TextFormat  
<b>toTextFormat</b>(); 
/** 
* Sets the text font. 
* @param font The desired font 
* @return This builder object to allow chaining calls 
*/ 
public  
<b>TextFormatBuilder</b> setFont(Font font); 
...
```
