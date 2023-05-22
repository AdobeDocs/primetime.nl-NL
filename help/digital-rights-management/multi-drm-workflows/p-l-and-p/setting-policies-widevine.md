---
title: Uitvoerbeveiligingsbeleid gebruiken
description: Uitvoerbeveiligingsbeleid gebruiken
copied-description: true
exl-id: d91c9181-a6b2-4982-a3ba-57c4b56428eb
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Uitvoerbeveiligingsbeleid gebruiken{#using-output-protection-policies}

**Beleid ter bescherming van de wijnproductie**

Widevine ondersteunt native zowel analoge als digitale uitvoerbeschermingsbeperkingen. Raadpleeg de documentatie van uw Widevine-serviceprovider over hoe u dit beleid aan gegenereerde licenties kunt koppelen.

Als u Expressplay als de Windows-serviceprovider gebruikt, voegt u een beleid voor de bescherming van de digitale uitvoer toe tijdens het genereren van tokens via de hdcpOutputControl-vlag: Toegestane waarden zijn 0, 1, 2 waarbij 0 = HDCP_NONE, 1 = HDCP_V1, 2 = HDCP_V2. Zowel HDCP_V1 als HDCP_V2 dwingen HDCP versie 1.X en 2.X af.

Expressplay biedt momenteel geen ondersteuning voor het koppelen van analoge uitvoerbeperkingen

**Beleid ter bescherming van PlayReady-uitvoer**

PlayReady biedt ook native ondersteuning voor beperkingen op het beschermen van analoge en digitale uitvoer. De waarden voor het uitvoerbeveiligingsniveau die u kunt instellen. De pagina [Uitvoerbeveiligingsniveaus](https://msdn.microsoft.com/en-us/library/dn468831.aspx) documenteert de waarden die u kunt plaatsen en hun verwacht cliëntgedrag.

Als u Expressplay gebruikt, koppelt u waarden voor het uitvoerbeveiligingsniveau bij het genereren van het token via de markering compressedDigitalAudioOPL, uncompressedDigitalAudioOPL, compressedDigitalVideoOPL, uncompressedDigitalVideoOPL en de markering unknownOutputBehavior. Deze worden beschreven op [PlayReady Verzoek voor token voor licentie](https://www.expressplay.com/developer/restapi/#playready-license-token-request)
