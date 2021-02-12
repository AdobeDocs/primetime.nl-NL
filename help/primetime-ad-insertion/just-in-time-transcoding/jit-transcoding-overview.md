---
title: Just-in-Time Transcoding
description: null
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Just-in-Time Transcoding {#just-in-time-transcoding}

Primetime Ad Insertion beschikt over just-in-time transcodering en verpakking om ervoor te zorgen dat incompatibele en creatieve elementen correct kunnen worden afgespeeld in inhoudsstromen. Het kan ID3 pakketten in en fragmenten injecteren die in cliënt-kant en het volgen kunnen worden gebruikt.
Een typisch werkschema is als volgt:

1. Adobe Primetime Ad Insertion haalt advertenties/creatieven van de advertentieserver van de klant op.

1. Als de creatieve indeling van een advertentie standaard compatibel is met de inhoudsstroom, wordt de creatieve indeling in het manifest ingevoegd.

1. Als de creatieve indeling van een advertentie niet standaard compatibel is (bijvoorbeeld .mp4, .mov, .webm), zoekt Primetime Ad Insertion naar een vooraf getranscodeerde versie van de advertentie vanuit een opgegeven CDN. Indien een dergelijke advertentie wordt gevonden, wordt die advertentie ingevoegd; anders, wordt de advertentie een rij gevormd voor transcode.

1. Nadat de creatieve advertentie is getranscodeerd, zal Primetime Ad Insertion alle verdere verzoeken om die advertentie in manifesten vastzetten.

Primetime Ad Insertion ondersteunt transcodering voor de meeste video- en lineaire indelingen. De creatieve transcodering vindt meestal binnen drie minuten plaats. Neem voor meer informatie contact op met uw ondersteuningsvertegenwoordiger voor Primetime.
