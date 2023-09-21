---
title: Codeermodule van derden gebruiken
description: Codeermodule van derden gebruiken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Codeermodule van derden gebruiken{#use-a-third-party-encoder}

Sommige klanten hebben reeds een pijpleiding van de inhoudsvoorbereiding op zijn plaats, gebruikend hardware of software videocoder (of Adobe Media Server). Als dit het geval is, kan elk product dat momenteel met Primetime DRM beveiligde inhoud kan maken, inhoud verpakken voor Primetime Cloud DRM met dezelfde configuratie-instellingen als de Primetime Cloud DRM Protection Kit. De vereiste informatie kan uit één van beide bestaande configuratiedossiers worden verkregen inbegrepen in de uitrusting: [!DNL config_hls.xml] of [!DNL config_hds.xml].

De relevante configuratiepunten zijn:

* URL licentieserver
* URL sleutelserver
* Certificaat van licentieserver
* Vervoerscertificaat
