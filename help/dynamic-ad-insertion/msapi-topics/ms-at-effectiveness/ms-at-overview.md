---
description: De meeste adverteerders hebben gedetailleerde informatie nodig over wanneer, hoe lang en hoe goed hun advertenties zijn bekeken. De meest efficiënte manier is om de clientspeler rapporten te laten verzenden terwijl de advertenties worden afgespeeld, maar de manifestserver ondersteunt ook server-side en hybride advertentie-tracking.
seo-description: De meeste adverteerders hebben gedetailleerde informatie nodig over wanneer, hoe lang en hoe goed hun advertenties zijn bekeken. De meest efficiënte manier is om de clientspeler rapporten te laten verzenden terwijl de advertenties worden afgespeeld, maar de manifestserver ondersteunt ook server-side en hybride advertentie-tracking.
seo-title: Advertentie bijhouden
title: Advertentie bijhouden
uuid: 184b8c36-5e51-42a7-b905-53f2b7b15e49
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Advertentie bijhouden {#ad-tracking}

De meeste adverteerders hebben gedetailleerde informatie nodig over wanneer, hoe lang en hoe goed hun advertenties zijn bekeken. De meest efficiënte manier is om de clientspeler rapporten te laten verzenden terwijl de advertenties worden afgespeeld, maar de manifestserver ondersteunt ook server-side en hybride advertentie-tracking.

Bij het inschakelen en volgen van de client wordt een van de volgende methoden gebruikt:

* **De client verzendt de client samen** met de op de advertentie geplaatste afspeellijst een JSON-, VMAP- of in-manifest-structuur die gebeurtenissen en URL&#39;s opgeeft. Deze methode is compatibel met het Interactive Advertising Bureau (IAB)

* **Serverzijde** De client neemt niet deel aan advertentie-tracking. De server verzendt alle gegevens voor het bijhouden van advertenties. Trackinggegevens worden alleen berekend aan de serverzijde en komen mogelijk niet overeen met de afspeelactiviteit aan de clientzijde. Bijvoorbeeld, als een eindgebruiker niet de volledige advertentie bekijkt, nadat de segmenten worden geleverd, overweegt de server nog de te spelen advertentie.

* **Hybride** dit is als cliënt-zijvolgen, maar de cliënt verzendt zijn rapporten naar de manifestserver, die hen aan aangewezen URLs opnieuw begeeft. Adverteerders ontvangen dezelfde informatie als bij het bijhouden van clientgegevens. In deze modus kunnen clients met beperkte internettoegang werken.