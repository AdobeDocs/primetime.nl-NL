---
title: Crossdomain-beleidsbestand
description: Crossdomain-beleidsbestand
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Crossdomain policy file {#crossdomain-policy-file}

Als de licentieserver wordt gehost op een ander domein dan het SWF-bestand voor het afspelen van video, is een bestand met interdomeinbeleid (crossdomain.xml) nodig om het SWF-bestand de mogelijkheid te geven licenties aan te vragen bij de licentieserver. Een bestand met interdomeinbeleid is een XML-bestand waarmee de server kan aangeven dat de gegevens en documenten ervan beschikbaar zijn voor SWF-bestanden die vanuit andere domeinen worden aangeboden. Elk SWF-bestand dat wordt aangeboden vanuit een domein dat is opgegeven in het bestand met interdomeinbeleid van de licentieserver, heeft toegang tot gegevens of elementen van die licentieserver.

Adobe raadt ontwikkelaars aan de best practices te volgen bij het implementeren van het bestand met interdomeinbeleid door vertrouwde domeinen alleen toegang te verlenen tot de licentieserver en de toegang tot de submap met licentie op de webserver te beperken.

Raadpleeg de volgende locaties voor meer informatie over domeinoverschrijdende beleidsbestanden:

* Controlemiddelen voor websites (beleidsbestanden)
* Specificatie van bestand voor interdomeinbeleid: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

