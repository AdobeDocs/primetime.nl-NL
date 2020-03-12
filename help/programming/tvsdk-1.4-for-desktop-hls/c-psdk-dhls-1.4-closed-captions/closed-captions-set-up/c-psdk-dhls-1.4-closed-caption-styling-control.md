---
description: U kunt opmaakinformatie voor ClosedCaptionStyles-tracks opgeven met de klasse ClosedCaptionStyles. Hiermee stelt u de stijl in voor alle gesloten bijschriften die door de speler worden weergegeven.
seo-description: U kunt opmaakinformatie voor ClosedCaptionStyles-tracks opgeven met de klasse ClosedCaptionStyles. Hiermee stelt u de stijl in voor alle gesloten bijschriften die door de speler worden weergegeven.
seo-title: Opmaak van ondertiteling beheren
title: Opmaak van ondertiteling beheren
uuid: 506c06d3-8fe0-46c9-9ed6-5b35d21c021c
translation-type: tm+mt
source-git-commit: b67a9dcb0abb07f4fdff4e03d9d6c0b07ff45127

---


# Opmaak van ondertiteling beheren{#control-closed-caption-styling}

U kunt opmaakinformatie voor ClosedCaptionStyles-tracks opgeven met de klasse ClosedCaptionStyles. Hiermee stelt u de stijl in voor alle gesloten bijschriften die door de speler worden weergegeven.

Deze klasse omvat opmaakgegevens voor Closed Caption-objecten, zoals het lettertype, de tekengrootte, de kleur en de achtergronddekking. Een bijbehorende hulpklasse, `ClosedCaptionStylesBuilder`vergemakkelijkt het werken met de montages van de gesloten-titelstijl.

## Stijlen voor een gesloten bijschrift instellen {#section_DAE84659D1964DB1B518F91B59AF29D9}

U kunt de tekst met een gesloten bijschrift opmaken met de methoden TVSDK.

1. Wacht op MediaPlayer om minstens de VOORBEREID status (zie [Wacht op een geldige staat](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-ui-configure/t-psdk-dhls-1.4-ui-state-prepared-wait-for.md)) te hebben.
1. Voer een van de volgende handelingen uit om de stijlinstellingen te wijzigen:

   * Gebruik de `ClosedCaptionStylesBuilder` `ClosedCaptionStyles` hulplijnklasse (werkt achter de schermen).
   * Gebruik de `ClosedCaptionStyles` klasse rechtstreeks.

>[!NOTE]
>
>Het instellen van de stijl voor een Closed Caption is een asynchrone bewerking, zodat het enkele seconden kan duren voordat de wijzigingen op het scherm worden weergegeven.

## Opties voor de stijl van gesloten bijschriften {#section_D28F50B98C0D48CF89C4FB6DC81C5185}

Met de `ClosedCaptionStyles` klasse kunt u opmaakinformatie opgeven voor Closed Caption-tracks. Hiermee stelt u de stijl in voor alle gesloten bijschriften die door de speler worden weergegeven.

```
public function TextFormat( 
   font:String = default,  
   size:String = default,  
   fontEdge:String = default,  
   fontColor:String = default,  
   backgroundColor:String = default,  
   fillColor:String = default,  
   edgeColor:String = default,  
   fontOpacity:int,  
   backgroundOpacity:int,  
   fillOpacity:int)
```

>[!TIP]
>
>In opties die standaardwaarden definiëren (bijvoorbeeld `DEFAULT`), verwijst die waarde naar de instelling op het moment dat het bijschrift oorspronkelijk werd opgegeven.

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
   <td colname="2"> <p>Het lettertype. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de <span class="codeph"> ClosedCaptionStyles.FONT- </span> array en die bijvoorbeeld een vaste spatiëring met of zonder schreef vertegenwoordigt. 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;FONT&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;AVCaptionStyle.MONOSPACE_WITH_SERIFS, 
      &nbsp;AVCaptionStyle.MONOSPACED_WITHOUT_SERIFS, 
      &nbsp;AVCaptionStyle.PROPORTIONAL_WITH_SERIFS, 
      &nbsp;AVCaptionStyle.PROPORTIONAL_WITHOUT_SERIFS, 
      &nbsp;AVCaptionStyle.CASUAL, 
      &nbsp;AVCaptionStyle.CURSIVE, 
      &nbsp;AVCaptionStyle.SMALL_CAPITALS 
      &nbsp;]; 
     </code> </p> <p>Tip:  De werkelijke lettertypen die op een apparaat beschikbaar zijn, kunnen variëren en waar nodig worden vervangende lettertypen gebruikt. Monospace met schreef wordt typisch gebruikt als substituut, hoewel deze substitutie systeemspecifiek kan zijn. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Grootte </td> 
   <td colname="2"> <p>De grootte van het bijschrift. </p> <p> Kan alleen worden ingesteld op een waarde die is gedefinieerd door de <span class="codeph"> ClosedCaptionStyles.FONT_SIZE- </span> array: 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> - De standaardgrootte </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> GROOT </span> - ongeveer 30% groter dan gemiddeld </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> KLEINE </span> - ongeveer 30% kleiner dan gemiddeld </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> STANDAARD </span> - De standaardgrootte voor het bijschrift; gelijk aan medium </li> 
     </ul> </p> <p>Tip:  U kunt de tekengrootte van WebVTT-bijschriften wijzigen door de grootteparameter voor de <span class="codeph"> instellingenfunctie DefaultMediaPlayer.ccStyles te wijzigen </span> . </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fontrand </td> 
   <td colname="2"> <p>Het effect dat voor de fontrand wordt gebruikt, zoals verhoogd of geen. </p> <p>Kan alleen worden ingesteld op een waarde die wordt gedefinieerd door de <span class="codeph"> ClosedCaptionStyles.FONT_EDGE- </span> array. 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;FONT_EDGE&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.NONE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RAISED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEPRESSED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.UNIFORM, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.LEFT_DROP_SHADOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RIGHT_DROP_SHADOW 
      &nbsp;]; 
     </code> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> Fontkleur </td> 
   <td colname="2"> <p>De fontkleur. </p> <p>Kan alleen worden ingesteld op een waarde die is gedefinieerd door de <span class="codeph"> ClosedCaptionStyles.COLOR- </span> array. 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;COLOR&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BLACK, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.GRAY, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.WHITE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_WHITE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.CYAN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_CYAN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_CYAN&nbsp;&nbsp;&nbsp;]; 
     </code> </p> </td> 
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
   <td colname="2"> <p>De kleur van de achtergrond van het venster waarin de tekst zich bevindt. </p> <p>Kan worden ingesteld op alle waarden die beschikbaar zijn voor de lettertypekleur. </p> <p>Belangrijk:  Dit is niet van toepassing op WebVTT-bijschriften, omdat WebVTT deze functie niet gebruikt. </p> </td> 
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
 </tbody> 
</table>

## Voorbeelden: Opmaak bijschrift {#section_63E33840B7A14D26990046E2ACF2ECA1}

U kunt opmaak voor Closed Caption opgeven.

## Voorbeeld 1: Opmaakwaarden expliciet opgeven {#section_BD7B48F3B66D4E9290E1CB2F464E08E4}

```
private function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    var formatBuilder:TextFormatBuilder = new TextFormatBuilder(); 
    formatBuilder.font = Font.DEFAULT,  
    formatBuilder.fontSize = FontSize.DEFAULT,  
    formatBuilder.fontEdge = FontEdge.DEFAULT,  
    formatBuilder.fontColor = Color.DEFAULT,  
    formatBuilder.backgroundColor = Color.DEFAULT,  
    formatBuilder.fillColor = Color.DEFAULT,  
    formatBuilder.edgeColor = Color.DEFAULT,  
    formatBuilder.fontOpacity = .DEFAULT_OPACITY,  
    formatBuilder.backgroundOpacity = Font.DEFAULT_OPACITY,  
    formatBuilder.fillOpacity = TextFormat.DEFAULT_OPACITY 
    mediaPlayer.set CCStyle(formatBuilder.toTextFormat()); 
} 
```

## Voorbeeld 2: Opmaakwaarden opgeven in parameters {#section_147036D7C31C4010A5A7DF49997014A9}

```
/** 
* Constructor using parameters to initialize a TextFormat. 
* 
* @param font 
* The desired font. 
* @param fontSize 
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
public function TextFormatBuilder(font:Font, fontSize:FontSize, fontEdge:FontEdge,  
                                  fontColor:Color, backgroundColor:Color,  
                                  fillColor:Color, edgeColor:Color, fontOpacity:int, 
                                  backgroundOpacity:int, fillOpacity:int); 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public function toTextFormat():TextFormat; 
... 
```
