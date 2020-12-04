---
description: Met de klasse TextFormat kunt u opmaakinformatie opgeven voor Closed Caption-tracks. Hiermee stelt u de stijl in voor alle gesloten bijschriften die door de speler worden weergegeven.
seo-description: Met de klasse TextFormat kunt u opmaakinformatie opgeven voor Closed Caption-tracks. Hiermee stelt u de stijl in voor alle gesloten bijschriften die door de speler worden weergegeven.
seo-title: Opmaak van ondertiteling beheren
title: Opmaak van ondertiteling beheren
uuid: 331b0833-3e8a-482e-a3df-5e92b69d0a94
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 0%

---


# Besturingselement voor closed-caption {#control-closed-caption-styling-overview}

Met de klasse TextFormat kunt u opmaakinformatie opgeven voor Closed Caption-tracks. Hiermee stelt u de stijl in voor alle gesloten bijschriften die door de speler worden weergegeven.

Deze klasse omvat opmaakgegevens voor Closed Caption-objecten, zoals het lettertype, de tekengrootte, de kleur en de achtergronddekking. Een gekoppelde hulpklasse, `TextFormatBuilder`, vergemakkelijkt het werken met de stijlinstellingen voor een gesloten bijschrift.

## Stijlen voor een gesloten bijschrift instellen {#set-closed-caption-styles}

U kunt de tekst met een gesloten bijschrift opmaken met de methoden TVSDK.

1. Wacht tot de mediaspeler zich ten minste in de staat PREPARED bevindt.
1. Maak een `TextFormatBuilder`-instantie.

   U kunt nu alle opmaakparameters voor een gesloten bijschrift opgeven of deze later instellen.

   TVSDK kapselt uit een gesloten bijschrift opmaakinformatie in de interface `TextFormat` in. De klasse `TextFormatBuilder` maakt objecten die deze interface implementeren.

   ```java
   public TextFormatBuilder( 
      Font font, 
      Size size, 
      FontEdge fontEdge, 
      Color fontColor, 
      Color backgroundColor, 
      Color fillColor, 
      Color edgeColor, 
      int fontOpacity, 
      int backgroundOpacity, 
      int fillOpacity)
   ```

1. Om een verwijzing naar een voorwerp te verkrijgen dat de `TextFormat` interface uitvoert, roep `TextFormatBuilder.toTextFormat` openbare methode.

   Hiermee wordt een `TextFormat`-object geretourneerd dat op de mediaspeler kan worden toegepast.

   ```java
   public TextFormat toTextFormat()
   ```

1. U kunt desgewenst de huidige stijlinstellingen voor een gesloten bijschrift ophalen door een van de volgende handelingen uit te voeren:

   * Haal alle stijlinstellingen op met `MediaPlayer.getCCStyle`.

      De terugkeerwaarde is een geval van de `TextFormat` interface.

      ```js
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws IllegalStateException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws IllegalStateException;
      ```

   * Krijg de montages één voor één door de `TextFormat` methodes van de interfaceteller.

      ```js
      public Color getFontColor(); 
      public Color getBackgroundColor(); 
      public Color getFillColor(); // retrieve the font fill color 
      public Color getEdgeColor(); // retrieve the font edge color 
      public Size getSize(); // retrieve the font size 
      public FontEdge getFontEdge(); // retrieve the font edge type 
      public Font getFont(); // retrieve the font type 
      public int getFontOpacity(); 
      public int getBackgroundOpacity();
      ```

1. Voer een van de volgende handelingen uit om de stijlinstellingen te wijzigen:

   >[!NOTE]
   >
   >U kunt de grootte van WebVTT-bijschriften niet wijzigen.

   * Gebruik de settermethode `MediaPlayer.setCCStyle`, die een geval van de `TextFormat` interface overgaat:

      ```js
      /** 
      * Sets the closed captioning style. Used to control the closed captioning font, 
      * size, color, edge and opacity.  
      * 
      * This method is safe to use even if the current media stream doesn't have closed 
      * captions. 
      * 
      * @param textFormat 
      * @throws IllegalStateException 
      */ 
      public void setCCStyle(TextFormat textFormat) throws IllegalStateException;
      ```

   * Gebruik de klasse `TextFormatBuilder`, die afzonderlijke settermethoden definieert.

      De interface `TextFormat` definieert een onveranderlijk object, zodat er alleen methoden getter en geen setters zijn. U kunt de opmaakparameters voor Closed Caption alleen instellen met de klasse `TextFormatBuilder`:

      ```js
      // set font type 
      public void setFont(Font font)  
      public void setBackgroundColor(Color backgroundColor) 
      public void setFillColor(Color fillColor) 
      // set the font-edge color 
      public void setEdgeColor(Color edgeColor)  
      // set the font size 
      public void setSize(Size size)  
      // set the font edge type 
      public void setFontEdge(FontEdge fontEdge)  
      public void setFontOpacity(int fontOpacity) 
      public void setBackgroundOpacity(int backgroundOpacity) 
      // set the font-fill opacity level 
      public void setFillOpacity(int fillOpacity)  
      public void setFontColor(Color fontColor)
      ```

Het instellen van de stijl voor een Closed Caption is een asynchrone bewerking. Het kan dus enkele seconden duren voordat de wijzigingen op het scherm worden weergegeven.

## Opties voor de stijl van een gesloten bijschrift {#closed-caption-styling-options}

U kunt meerdere opties voor de bijschriftstijl opgeven. Deze opties overschrijven de stijlopties in de originele bijschriften

```
public TextFormatBuilder(
 Font font,
 Size size,
 FontEdge fontEdge,
 Color fontColor,
 Color backgroundColor,
 Color fillColor,
 Color edgeColor,
 int fontOpacity,
 int backgroundOpacity,
 int fillOpacity,
 String bottomInset)
```

>[!TIP]
>
>In opties die standaardwaarden definiëren (bijvoorbeeld DEFAULT), verwijst die waarde naar de instelling op het moment dat de ondertitel oorspronkelijk werd opgegeven.

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> Indeling </b></th> 
   <th colname="2" class="entry"> <b>Beschrijving</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> Lettertype </td> 
   <td colname="2"> <p>Het lettertype. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de opsomming <span class="codeph"> TextFormat.Font </span> en die bijvoorbeeld een vaste spatiëring met of zonder schreef vertegenwoordigt. </p> <p>Tip:  De werkelijke lettertypen die op een apparaat beschikbaar zijn, kunnen variëren en waar nodig worden vervangende lettertypen gebruikt. Monospace met schreef wordt typisch gebruikt als substituut, hoewel deze substitutie systeemspecifiek kan zijn. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Grootte </td> 
   <td colname="2"> <p>De grootte van het bijschrift. </p> <p> Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de opsomming <span class="codeph"> TextFormat.Size </span>: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM  </span> - De standaardgrootte </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROOT  </span> - ongeveer 30% groter dan gemiddeld </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEIN  </span> - ongeveer 30% kleiner dan gemiddeld </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDAARD  </span> - De standaardgrootte voor het bijschrift; gelijk aan medium </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fontrand </td> 
   <td colname="2"> <p>Het effect dat voor de fontrand wordt gebruikt, zoals verhoogd of geen. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de opsomming <span class="codeph"> TextFormat.FontEdge </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fontkleur </td> 
   <td colname="2"> <p>De fontkleur. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de opsomming <span class="codeph"> TextFormat.Color </span>. </p> </td> 
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
   <td colname="2"> <p>De dekking van de tekst. </p> <p>Uitgedrukt als een percentage tussen 0 (volledig transparant) en 100 (volledig dekkend). <span class="codeph"> DEFAULT_OPACITY  </span> voor het lettertype is 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Achtergronddekking </td> 
   <td colname="2"> <p>De dekking van de cel van het achtergrondteken. </p> <p>Uitgedrukt als een percentage tussen 0 (volledig transparant) en 100 (volledig dekkend). <span class="codeph"> DEFAULT_OPACITY  </span> voor de achtergrond is 100. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Vuldekking </td> 
   <td colname="2"> <p>De dekking van de achtergrond van het bijschriftvenster. </p> <p>Uitgedrukt als een percentage tussen 0 (volledig transparant) en 100 (volledig dekkend). <span class="codeph"> DEFAULT_OPACITY  </span> voor vulling is 0. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Voorbeelden van bijschriftopmaak {#examples-caption-formatting}

U kunt opmaak voor Closed Caption opgeven.

**Voorbeeld 1: Opmaakwaarden expliciet opgeven**

```java
private final MediaPlayer.PlaybackEventListener  
  _playbackEventListener = new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // Set CC style. 
        TextFormat tf = new TextFormatBuilder(TextFormat.Font.DEFAULT, 
        TextFormat.Size.DEFAULT, 
        TextFormat.FontEdge.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
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
public TextFormatBuilder( 
    Font font, Size size, FontEdge fontEdge, 
    Color fontColor, Color backgroundColor,  
    Color fillColor, Color edgeColor, 
    int fontOpacity, int backgroundOpacity, 
    int fillOpacity); 
 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public TextFormat toTextFormat(); 
 
/** 
* Sets the text font. 
* @param font The desired font 
* @return This builder object to allow chaining calls 
*/ 
public TextFormatBuilder setFont(Font font); 
... 
```
