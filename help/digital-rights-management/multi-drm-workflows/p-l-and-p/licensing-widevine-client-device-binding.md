---
description: In sommige gevallen wilt u wellicht voorkomen dat eindgebruikers inhoud afspelen op meerdere apparaten wanneer de inhoud wordt aangeschaft of gehuurd. Als de klant Expressplay gebruikt, kan dit worden gedaan door de Uitdrukkelijke APIs te gebruiken om het teken van de Uitdrukking van de gebruiker aan de machine van de gebruiker te binden.
title: Apparaatbinding
exl-id: 96ead794-e3eb-4059-91d3-a2c351a17ea3
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Apparaatbinding{#device-binding}

In sommige gevallen wilt u wellicht voorkomen dat eindgebruikers inhoud afspelen op meerdere apparaten wanneer de inhoud wordt aangeschaft of gehuurd. Als de klant Expressplay gebruikt, kan dit worden gedaan door de Uitdrukkelijke APIs te gebruiken om het teken van de Uitdrukking van de gebruiker aan de machine van de gebruiker te binden.

U kunt de API&#39;s op de volgende manier gebruiken.

1. Genereer een cookie.
1. Verzend een dummy verzoek voor het genereren van een token met het gegenereerde cookie als een querytekenreeks (cookie=`<cookie>`) of als kopteksten.
1. Laat de computer van de gebruiker een licentieaanvraag naar de expresslicentieserver verzenden met behulp van het bovenstaande token, bijvoorbeeld door een dummyinhoud af te spelen.

   Deze dummy vergunningsaanvraag, wanneer succesvol, associeert device_id van de gebruiker (die door de implementatie DRM op het apparaat van de gebruiker wordt berekend of geproduceerd) aan het koekje in het terug-eind van de Uitdrukking wordt berekend. Deze cookie wordt vervolgens op de volgende manier gebruikt:

   * Bij de aankoop/huurtijd van de inhoud, vraagt de code het terug-eind van de Uitdrukking voor device_id van de gebruiker door het bijbehorende koekje te verzenden ( [https://www.expressplay.com/developer/restapi/#record-retrieval](https://www.expressplay.com/developer/restapi/#record-retrieval))
   * Verzend een verzoek van de symbolische generatie met de gekochte sleutel van de inhoud (CEK), keyID (CEKSID), beleid, en andere informatie, vastmakend het koekje en device_id hierboven als, respectievelijk, `cookie` correlatieparameter en `deviceid` parameter voor tokenbeperking.

   * Geef deze token op aan de gebruiker.

      Dit proces produceert een teken voor de inhoud die aan device_id van de gebruiker wordt gebonden. Wanneer de machine van de gebruiker een vergunningsverzoek met dit teken verzendt, zal het de achterste eind van de Uitdrukking apparaat_id van het teken met device_id van het vergunningsverzoek kruisen.

      Deze workflow wordt geïmplementeerd door een voorbeeldexpressmachtiging-server.
