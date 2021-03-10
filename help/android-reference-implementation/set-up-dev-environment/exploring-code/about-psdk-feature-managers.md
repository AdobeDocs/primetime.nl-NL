---
title: Functiemanagers
description: De managers van de eigenschap verstrekken een manier voor u om individuele eigenschappen te controleren zonder volledige TVSDK in onderzoek naar code voor één eigenschap over te steken die in veelvoudige plaatsen zou kunnen worden verspreid.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---


# Functiemanagers {#feature-managers}

De managers van de eigenschap verstrekken een manier voor u om individuele eigenschappen te controleren zonder volledige TVSDK in onderzoek naar code voor één eigenschap over te steken die in veelvoudige plaatsen zou kunnen worden verspreid. Functiemanagers beperken code tot één klasse per functie. De eigenschapmanagers wachten op trekkers van gebeurtenissen TVSDK en informeren dan de klasse die de eigenschapmanager gebruikt om het resultaat te behandelen. De functiemanager verstrekt de vereiste informatie aan de klasse.

De eigenschapmanagers voeren de volgende taken uit:

* **Triggers TVSDK-functies.**
Dit zijn functieaanroepen om een TVSDK-functie te activeren. Bijvoorbeeld: 
`PlaybackManager.play()` wordt aangeroepen wanneer de toepassing van de speler het afspelen van de video moet starten.

* **Luistert naar TVSDK-gebeurtenissen.**
De functiemanager moet naar gebeurtenissen van TVSDK luisteren om informatie van TVSDK te verwerven. Bijvoorbeeld: 
`AdsManager` luistert naar TVSDK Ads-gebeurtenissen die op de hoogte moeten worden gebracht wanneer de advertentie wordt gestart.

* **Verzendt gebeurtenissen naar de manager.**
Nadat de eigenschapmanagers de gebeurtenissen van TVSDK ontvangen en verwerken, brengen zij de cliëntkant op om de gebeurtenis te behandelen. Bijvoorbeeld na 
`AdsManager` ontvangt een gebeurtenis van het begin van het advertentieverlies, vertelt het spelerfragment om deze verandering in UI (onbruikbaar maken schrobt bar, toon de advertentie bedekking, enz.) te weerspiegelen.

De implementatie van de Primetime-verwijzing omvat de volgende functiemanagers:

| Functiebeheer | Standaardbestand | Functie |  |
|---|---|---|---|
| Video afspelen | PlaybackManager | Afspelen en besturing van HLS, afspelen en besturen van DVR, bufferbeheer en verwerking van multi-bitsnelheden. | Vereist |
| DRM-inhoudsbeveiliging | DRmManager | Inhoudsbescherming. | Vereist |
| Toevoegen | AdsManager | Toevoegen, inclusief Adobe Primetime en directe en onderbreking van beslissingen, en aangepaste ad-onderbreking. | Optioneel |
| Ondertiteling | CCManager | Ondertiteling en ondertitels van VTT gesloten. | Optioneel |
| Geluid met late binding | AAManager | Geluid laat inbinden. | Optioneel |
| QoS | QosManager | QoS-statistieken. | Optioneel |
| Entitlement | EntitlementManager | Primetime integratie van verificatierechten. | Optioneel |

De voorbeeldimplementatie bevat basisstandaardklassen, die hierboven worden vermeld, en corresponderende klassen met het achtervoegsel Aan. De standaardklassen bieden het standaardgedrag van TVSDK, terwijl de klassen met het achtervoegsel Aan alle code bevatten die is vereist om de TVSDK-functie te activeren en te luisteren naar TVSDK-gebeurtenissen voor die functie.

* Voor optionele functies werkt de standaardcode alsof deze is uitgeschakeld.
* Klassen met het achtervoegsel Aan werken alsof de functie is ingeschakeld.