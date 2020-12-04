---
seo-title: Crossdomain DRM-beleidsbestand
title: Crossdomain DRM-beleidsbestand
uuid: cb91a85a-1825-4fd7-a25c-880cdbd5c8b8
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Crossdomain DRM-beleidsbestand {#crossdomain-drm-policy-file}

Als de licentieserver wordt gehost op een ander domein dan het SWF-bestand voor het afspelen van video, is een DRM-beleidsbestand voor meerdere domeinen ( [!DNL crossdomain.xml]) nodig om het SWF-bestand in staat te stellen licenties aan te vragen bij een licentieserver. Een domeinoverschrijdend DRM-beleidsbestand wordt vertegenwoordigd door een XML-bestand waarmee de server kan aangeven dat de gegevens en documenten ervan beschikbaar zijn voor SWF-bestanden die vanuit andere domeinen worden aangeboden. Elk SWF-bestand dat wordt aangeboden vanuit een domein dat is opgegeven in het DRM-beleidsbestand voor meerdere domeinen van de licentieserver, heeft toegang tot gegevens of elementen van die licentieserver.

Adobe raadt ontwikkelaars aan de best practices te volgen bij het implementeren van het bestand met interdomeinbeleid door vertrouwde domeinen alleen toegang te verlenen tot de licentieserver en de toegang tot de submap met licentie op de webserver te beperken.

Raadpleeg de volgende locaties voor meer informatie over domeinoverschrijdende DRM-beleidsbestanden:

* Controlemiddelen voor websites (DRM-beleidsbestanden)
* Specificatie van DRM-beleidsbestand voor meerdere domeinen: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

