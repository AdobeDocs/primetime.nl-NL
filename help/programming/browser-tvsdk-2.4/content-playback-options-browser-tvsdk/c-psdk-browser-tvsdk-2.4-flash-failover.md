---
description: Browser TVSDK biedt hulpprogramma's voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.
seo-description: Browser TVSDK biedt hulpprogramma's voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.
seo-title: 'null'
title: 'null'
uuid: 57b35a5f-87f8-41a2-ad85-300b999dc30b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# Flash-failover {#flash-failover}

Browser TVSDK biedt hulpprogramma&#39;s voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler), die u kunt integreren met andere Primetime-componenten.

Gebruik de gereedschappen van uw platform om een speler te maken en deze te verbinden met de weergave van de mediaspeler in Browser-TVSDK, die methoden bevat voor het afspelen en beheren van video&#39;s. Browser-TVSDK biedt bijvoorbeeld afspeel- en pauzemethoden. U kunt gebruikersinterfaceknoppen op uw platform tot stand brengen en de knopen plaatsen om die methodes te roepen Browser TVSDK.

## Flash fallback {#section_92D3884A13A6431F9A9CC5C79715D888}

In Browser-TVSDK werkt uw toepassing alleen met de `Primetime.js`-API. De onderliggende TVSDK-implementatie van de browser bepaalt welke spelertechnologie moet worden gebruikt op basis van het huidige platform en het mediatype dat moet worden afgespeeld.

De beslissing voor de spelertechnologie wordt niet genomen tot u `MediaPlayer.replaceCurrentResource` roept om een specifieke bron te spelen.

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
1. Gebruik, indien ondersteund, de tag `<video>` rechtstreeks zonder MSE.
1. Zorg ervoor dat u ten minste Adobe Flash Player 23.0 gebruikt.
1. Als geen geschikte playbacktechnologie wordt gevonden, `replaceCurrentResource` keert een fout terug.

Een volgende `replaceCurrentResource` vraag op de zelfde `MediaPlayer` instantie volgt het zelfde proces. Dit staat u toe om diverse middeltypes te spelen door de zelfde `MediaPlayer` instantie in de zelfde ouder `<DIV>` markering te gebruiken die u specificeerde toen de `MediaPlayerView` instantie werd gecreeerd.

>[!TIP]
>
>Het SWF-object en de tag `<video>` zijn genest in de bovenliggende tag `<DIV>`.

