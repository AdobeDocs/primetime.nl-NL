---
seo-title: Crossdomain-beleidsbestand
title: Crossdomain-beleidsbestand
uuid: fc05aa5e-6fbd-445f-a22a-f795d5a0b3ad
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Crossdomain-beleidsbestand {#crossdomain-policy-file}

Als de licentieserver wordt gehost op een ander domein dan het SWF-bestand voor het afspelen van video, is een bestand met interdomeinbeleid (crossdomain.xml) nodig om het SWF-bestand de mogelijkheid te geven licenties aan te vragen bij de licentieserver. Een bestand met interdomeinbeleid is een XML-bestand waarmee de server kan aangeven dat de gegevens en documenten ervan beschikbaar zijn voor SWF-bestanden die vanuit andere domeinen worden aangeboden. Elk SWF-bestand dat wordt aangeboden vanuit een domein dat is opgegeven in het bestand met interdomeinbeleid van de licentieserver, heeft toegang tot gegevens of elementen van die licentieserver.

Adobe raadt ontwikkelaars aan de best practices te volgen bij het implementeren van het bestand met interdomeinbeleid door vertrouwde domeinen alleen toegang te verlenen tot de licentieserver en de toegang tot de submap met licentie op de webserver te beperken.

Raadpleeg de volgende locaties voor meer informatie over domeinoverschrijdende beleidsbestanden:

* Controlemiddelen voor websites (beleidsbestanden)
* Specificatie van bestand voor interdomeinbeleid: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

