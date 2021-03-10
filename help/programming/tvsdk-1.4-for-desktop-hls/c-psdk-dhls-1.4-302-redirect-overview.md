---
description: 302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.
title: HTTP 302-herleidingsoptimalisatie
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 1%

---


# HTTP 302 herdirect optimization{#http-redirect-optimization}

302 optimalisatie voor omleiding minimaliseert het aantal van 302 reacties voor omleiding, waardoor uw toepassing de taakverdeling effectiever kan uitvoeren.

Als een hoofdmanifestverzoek wordt omgeleid, en optimalisering 302 in uw speler wordt toegelaten, zullen de verdere verzoeken die voor activa van dat manifest worden gemaakt de definitieve domeinplaats gebruiken, die extra 302 reacties vermijdt.

Deze functie is standaard uitgeschakeld en u kunt deze instelling wijzigen.

Als u deze eigenschap toelaat, werkt het correct slechts als *all* van de volgende voorwaarden waar zijn; anders vindt geen herleidingsoptimalisatie plaats en blijven 302 reacties optreden:

* Uw toepassing werd gecompileerd voor Adobe Flash Player 11.8, gebruikend `-swf-version` 21 of hoger.
* Uw eindgebruikers hebben Adobe Flash Player 11.8 of later geïnstalleerd.

>[!IMPORTANT]
>
>Schakel 302 omleiding uit om ervoor te zorgen dat cookies worden doorgegeven met advertentieverzoeken. Wanneer 302 omleiding wordt toegelaten, zou het advertentieverzoek aan een domein kunnen worden opnieuw gericht dat van het domein verschillend is waarvan de koekje voortkwam.

## 302 omleidingsoptimalisatie uitschakelen of inschakelen {#section_D6687FC44C61446F878008B629A5FA19}

Gebruik de eigenschap `useRedirectedUrl` om 302 omleiding in of uit te schakelen (true).

<!--<a id="example_B886777252B745AAB48B1FCC42C97A25"></a>-->

Bijvoorbeeld:

```
// Set useRedirectedUrl property to true 
var networkConfiguration = new NetworkConfiguration(); 
networkConfiguration.useRedirectedUrl = true; 
  
//Set NetworkConfiguration as Metadata: 
var result:Metadata = new Metadata(); 
result.setMetadata(DefaultMetadataKeys.NETWORK_CONFIGURATION_KEY,  
                   networkConfiguration); 
  
var mediaResource = new MediaResource( url, MediaResourceType.HLS, result); 
  
// load the resource 
mediaPlayer.replaceCurrentResource( mediaResource, mediaPlayerItemConfig );
```

