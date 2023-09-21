---
title: Crossdomain-beleidsbestand
description: Crossdomain-beleidsbestand
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Crossdomain-beleidsbestand {#crossdomain-policy-file}

Als de licentieserver op een ander domein wordt gehost dan de SWF voor het afspelen van video, is een bestand met interdomeinbeleid (crossdomain.xml) nodig om de SWF toe te staan licenties aan te vragen bij de licentieserver. Een bestand met interdomeinbeleid is een XML-bestand waarmee de server kan aangeven dat de gegevens en documenten ervan beschikbaar zijn voor SWF-bestanden die vanuit andere domeinen worden aangeboden. Elk SWF-bestand dat wordt aangeboden vanuit een domein dat is opgegeven in het bestand met interdomeinbeleid van de licentieserver, heeft toegang tot gegevens of elementen van die licentieserver.

Adobe raadt ontwikkelaars aan de best practices te volgen bij het implementeren van het bestand met interdomeinbeleid door vertrouwde domeinen alleen toegang te verlenen tot de licentieserver en de toegang tot de submap met licentie op de webserver te beperken.

Raadpleeg de volgende locaties voor meer informatie over domeinoverschrijdende beleidsbestanden:

* Controlemiddelen voor websites (beleidsbestanden)
* Specificatie van bestand voor interdomeinbeleid: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
