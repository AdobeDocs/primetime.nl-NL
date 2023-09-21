---
description: U kunt aangepaste tagnamen in een stream configureren met de MediaPlayerItemConfig-klasse.
title: Methoden van de klasse Config voor tags
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Methoden van de klasse Config voor tags{#config-class-methods-for-tags}

U kunt aangepaste tagnamen in een stream configureren met de MediaPlayerItemConfig-klasse.

Een nieuwe `MediaPlayerItemConfig`:

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

Hier is wat informatie over hoe `MediaPlayerItemConfig` methoden worden gebruikt voor het beheer van aangepaste tags:

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
   <td colname="col2"> <p>Hiermee stelt u de lijst met geabonneerde tags in die aan de toepassing worden blootgesteld. </p> <p>Uw toepassing wordt ook automatisch geabonneerd op alle tags die via <span class="codeph"> adTags </span>. </p> </td> 
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

* De aangepaste tagnaam moet de `#` voorvoegsel

  Bijvoorbeeld: `#EXT-X-ASSET` is een correcte aangepaste tagnaam, maar `EXT-X-ASSET` is onjuist.

* U kunt de configuratie niet wijzigen nadat de mediastream is geladen.
