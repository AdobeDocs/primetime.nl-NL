---
title: Ad Insertion gebruiken in Live/Lineaire stream
description: Ad Insertion gebruiken in Live/Lineaire stream
exl-id: d56ed723-ec72-4bbd-befc-6858c7c9d800
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Ad Insertion gebruiken in Live/Lineaire stream {#ad-insertion-live-linear-stream}

Met Primetime Ad Insertion kunnen uitgevers standaardsituaties en complexe situaties voor het invoegen van toevoegingen tijdens live/lineaire streams verwerken.

## Ondersteunde geluidsindelingen {#cue-formats-supported}

Primetime Ad Insertion ondersteunt een groot aantal standaard- en niet-standaard actiefindelingen, waaronder:

* DPI SCTE-35 (SCTE-35 verbeterde advertentiemarkeringen)

* [Adobe Digital Program Inserting Signaling Specification](https://www.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeDigitalProgramInsertionSignalingSpecification.pdf)

* Binair SCTE-35 (zowel HLS als DASH)

* Ware SCTE-35 (zowel HLS als DASH)

Neem contact op met de ondersteuningsvertegenwoordiger van Primetime voor meer informatie of andere ondersteunde actiefindelingen.

## Ondersteuning voor gedeeltelijk afbreken van advertenties {#partial-ad-break-support}

Gedeeltelijke advertentie-einden kunnen worden gebruikt in situaties waarin een viewer een live/lineaire stream invoert nadat een advertentie-einde is gestart.  Als een viewer bijvoorbeeld een lange versie van 2:00 invoert en een onderbreking van 1:00 invoert, zorgt de gedeeltelijke invoeging en de invoeging van onderbreking ervoor dat de advertenties in de resterende tijd worden weergegeven. Zonder gedeeltelijke invoeging in een advertentie, worden tijdens het einde geen advertenties naar deze viewer verzonden. Met Primetime Ad Insertion kunt u de invoeging van delen en afbrekingen standaard inschakelen als de juiste tags aanwezig zijn in de mediastream(s).

## Vroege terugkeer (Vroege Advertentie) {#early-return-early-ad-exit}

Er zijn gevallen waarin het nodig kan zijn vroegtijdig terug te keren vanaf een advertentie-einde in een live/lineaire stream, bijvoorbeeld wanneer een sportevenement plotseling weer in actie komt. Elke indelingen voor ad-beslissing bevat een tag naar &quot;cue-out&quot; (advertenties) of &quot;cue-in&quot; (inhoud).  Als een &#39;cue-in&#39;-tag wordt aangetroffen vóór het einde van een advertentiepauze, zal Adobe Primetime Ad Insertion de cue-in respecteren.  Neem contact op met uw inhoudspakket om vroege terugkeer in te schakelen.
