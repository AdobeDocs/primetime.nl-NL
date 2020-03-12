---
description: U kunt aangepaste tagnamen in een stream configureren met de MediaPlayerItemConfig-klasse.
seo-description: U kunt aangepaste tagnamen in een stream configureren met de MediaPlayerItemConfig-klasse.
seo-title: Methoden van de klasse Config voor tags
title: Methoden van de klasse Config voor tags
uuid: 222a0349-58d5-4bf3-9d03-e5920610faf5
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661

---


# Methoden van de klasse Config voor tags{#config-class-methods-for-tags}

U kunt aangepaste tagnamen in een stream configureren met de MediaPlayerItemConfig-klasse.

To create a new `MediaPlayerItemConfig`:

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

Hier volgt informatie over de manier waarop de `MediaPlayerItemConfig` methoden worden gebruikt om aangepaste tags te beheren:

<table id="table_0AC0973497144DDAB05726E3F031ACD1"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>Abonneren op specifieke aangepaste tags</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;subscribeTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>Hiermee wordt de huidige lijst met geabonneerde tags opgehaald. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;subscribeTags&nbsp;=&nbsp;["#EXT-X-PROGRAM-DATE-TIME"];mediaPlayerItemConfig.subscribeTags&nbsp;=&nbsp;subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>Hiermee stelt u de lijst met geabonneerde tags in die aan de toepassing worden blootgesteld. </p> <p>Uw toepassing wordt ook automatisch geabonneerd op alle tags die via <span class="codeph"> advertentietags worden verzonden </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>De advertentietags aanpassen die worden gebruikt door de standaardopportuniteitsdetector </b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;adTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.adTags; 
    </code> </td> 
   <td colname="col2"> <p>Hiermee wordt de huidige lijst met advertentietags opgehaald. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;adTags&nbsp;=&nbsp;["#EXT-X-CUE"];mediaPlayerItemConfig.adTags&nbsp;=&nbsp;adTags;
    </code> </td> 
   <td colname="col2"> <p>Hiermee stelt u de lijst met advertentietags in die door de standaardopportuniteitsgenerator moet worden gebruikt. </p> </td> 
  </tr> 
 </tbody> 
</table>

Houd rekening met het volgende:

* De aangepaste tagnaam moet het `#` voorvoegsel bevatten.

   De aangepaste tagnaam `#EXT-X-ASSET` is bijvoorbeeld correct, maar `EXT-X-ASSET` is onjuist.

* U kunt de configuratie niet wijzigen nadat de mediastream is geladen.

