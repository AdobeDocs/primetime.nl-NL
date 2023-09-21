---
description: Browser TVSDK biedt hulpprogramma's voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.
title: Flash-failover
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Flash-failover {#flash-failover}

Browser TVSDK biedt hulpprogramma&#39;s voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.

Gebruik de gereedschappen van uw platform om een speler te maken en deze te verbinden met de weergave van de mediaspeler in Browser-TVSDK, die methoden bevat voor het afspelen en beheren van video&#39;s. Browser-TVSDK biedt bijvoorbeeld afspeel- en pauzemethoden. U kunt gebruikersinterfaceknoppen op uw platform tot stand brengen en de knopen plaatsen om die methodes te roepen Browser TVSDK.

## Flash fallback {#section_92D3884A13A6431F9A9CC5C79715D888}

In Browser-TVSDK werkt uw toepassing alleen met de `Primetime.js` API. De onderliggende TVSDK-implementatie van de browser bepaalt welke spelertechnologie moet worden gebruikt op basis van het huidige platform en het mediatype dat moet worden afgespeeld.

De beslissing voor de spelertechnologie wordt pas genomen als je belt `MediaPlayer.replaceCurrentResource` om een specifieke bron af te spelen.

Bijvoorbeeld:

```js
var player = new AdobePSDK.MediaPlayer(), 
              mediaResource = new AdobePSDK.MediaResource(url, 
              AdobePSDK.MediaResource.Type.TYPE_HLS); 
              ... 
              player.replaceCurrentResource(mediaResource);
```

## De mediaspeler bepalen die moet worden gebruikt {#section_D844E386AF5848688D204DEE258ECEE6}

Deze voorbeeldprocedure illustreert het proces om de spelertechnologie te bepalen:

>[!TIP]
>
>Het proces kan afhankelijk van URL en uw milieu variëren.

1. Als de Uitbreidingen van de Bron van Media wordt gesteund, gebruik het zonder bekende beperkingen.
1. Gebruik, indien ondersteund, de `<video>` rechtstreeks zonder MSE.
1. Zorg ervoor dat u minstens versie 23.0 van de Flash Player van de Adobe gebruikt.
1. Als er geen geschikte afspeeltechnologie wordt gevonden, `replaceCurrentResource` retourneert een fout.

Een volgende `replaceCurrentResource` dezelfde oproep `MediaPlayer` -instantie volgt hetzelfde proces. Hierdoor kunt u verschillende typen bronnen afspelen door hetzelfde te gebruiken `MediaPlayer` instantie in hetzelfde bovenliggende `<DIV>` -tag die u hebt opgegeven bij het `MediaPlayerView` -instantie is gemaakt.

>[!TIP]
>
>Het object SWF en de `<video>` -tag is genest in het bovenliggende `<DIV>` -tag.
