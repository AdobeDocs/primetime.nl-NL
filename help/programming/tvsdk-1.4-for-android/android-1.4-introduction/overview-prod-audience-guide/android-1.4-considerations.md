---
description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
seo-description: Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.
seo-title: Overwegingen en beste praktijken
title: Overwegingen en beste praktijken
uuid: e698ae09-280b-4406-a9b8-4f468b7a6b9c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Overwegingen en beste praktijken{#considerations-and-best-practices}

Als u TVSDK het doeltreffendst wilt gebruiken, moet u bepaalde details van de werking van de SDK in overweging nemen en bepaalde best practices volgen.

## Overwegingen {#section_tvsdk_considerations}

Houd rekening met de volgende informatie wanneer u TVSDK gebruikt:

* Adobe Primetime werkt momenteel niet op Android-emulators.

   U moet echte apparaten gebruiken voor het testen.
* Afspelen wordt alleen ondersteund voor HLS-inhoud (HTTP Live Streaming).
* Hoofdvideo-inhoud kan worden vermenigvuldigd, waarbij video- en audiostreams zich in dezelfde uitvoering bevinden, of niet-gemultiplext, waarbij video- en audiostreams zich in afzonderlijke uitvoeringen bevinden.
* De TVSDK-API is geïmplementeerd in Java.
* Momenteel moet u de meeste API-bewerkingen voor TVSDK uitvoeren op de gebruikersinterfacethread. Dit is de belangrijkste Android-thread.

   De verrichtingen die correct op de belangrijkste draad lopen zouden een fout kunnen werpen en weggaan wanneer looppas op een achtergronddraad.
* Voor het afspelen van video&#39;s is de Adobe Video Engine (AVE) vereist. Dit beïnvloedt hoe en wanneer de media middelen kunnen worden betreden:

   * Ondertiteling met gesloten ondertiteling wordt gesteund in de mate die door AVE wordt verstrekt.
   * Afhankelijk van de precisie van de codeermodule kan de werkelijk gecodeerde mediaduur afwijken van de tijdsduur die in het manifest van de streambron wordt vastgelegd.

      Er is geen betrouwbare manier om tussen de ideale virtuele tijdlijn en de werkelijke afspeeltijdlijn opnieuw te synchroniseren. Bij het bijhouden van de voortgang van het afspelen van de stream voor advertentiebeheer en Video-analyse moet de werkelijke afspeeltijd worden gebruikt. Het is dus mogelijk dat de media en advertentie-inhoud niet exact worden bijgehouden door de rapportage en het gedrag van de gebruikersinterface.
   * Aan de naam van de inkomende gebruikersagent voor alle mediaverzoeken van de TVSDK op dit platform wordt het volgende tekenreekspatroon toegewezen:

      ```
      "Adobe Primetime/ + 
      <varname>
      originalUserAgent
      </varname>" 
      ```

      Voor alle aan advertenties gerelateerde aanroepen wordt de standaardgebruikersagent van Android of de aangepaste gebruikersagent gebruikt als u deze instelt tijdens het instellen van metagegevens voor invoegtoepassingen.

## Aanbevolen procedures {#section_tvsdk_best_practices}

Hier volgen de aanbevolen procedures voor TVSDK:

* Gebruik HLS versie 3.0 of hoger voor programma-inhoud.
* Voer de meeste bewerkingen van TVSDK uit in de hoofd (UI) draad, niet op achtergronddraden.
