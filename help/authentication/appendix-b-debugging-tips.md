---
title: Bijlage B "Tips voor foutopsporing"
description: Bijlage B "Tips voor foutopsporing"
exl-id: ea024797-315e-47c0-99ea-1ac49c8c9697
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Aanhangsel B: Tips voor foutopsporing {#appendix-b-debugging-tips}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.


## Tijdelijke gegevens wissen {#clearing-temporary-data}

Bij Adobe Primetime-verificatie worden tijdelijke gegevens opgeslagen, zoals browsercache, LSO&#39;s-cache en cookies. Het wissen van tijdelijke gegevens is belangrijk om ervoor te zorgen dat u bij het testen een schone lei krijgt.

- [De browsercache en cookies wissen](#clearing-the-browser-cache-and-cookies)
- [LSO&#39;s-cache wissen](#clearing-lsos-cache)\
    

## De browsercache en cookies wissen {#clearing-the-browser-cache-and-cookies}

Het is browser betrouwbaar, maar in Firefox: &quot;Gereedschappen&quot; -\> &quot;Recente geschiedenis wissen...&quot; -\> Voor &quot;Te wissen tijdbereik:&quot; selecteert u &quot;Alles&quot;; en op &quot;Details&quot;: Klik op &quot;Nu wissen&quot; en &quot;Cache&quot; -\>.\
 

## LSO&#39;s-cache wissen {#clearing-lsos-cache}

Toegang krijgen tot [Flash Player help](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html).

Selecteer ```entitlement.\*``` (afhankelijk van wat er wordt getest) en klik op &quot;Website verwijderen&quot;.\
 

## Foutopsporingsgereedschappen {#tools}

Adobe Primetime-verificatietechnici gebruiken de volgende tools voor foutopsporing:

- Firebug - <http://www.getfirebug.com/>
- Flashbug (werkt met de foutopsporingsversie van de Flash Player) <https://addons.mozilla.org/en-US/firefox/addon/14465/>
- Live http-headers - <https://addons.mozilla.org/en-US/firefox/addon/3829/>
- Fiddler - <http://www.fiddler2.com/fiddler2/>
- Charles - <http://www.charlesproxy.com/>
- Wireshark - <http://www.wireshark.org/>


<!--
## Related Information

- [Programmer Integration Guide](/help/authentication/programmer-integration-guide-overview.md)

- [Using Charles Proxy (Tech Note)](https://tve.zendesk.com/hc/en-us/articles/204962849-Using-Charles-Proxy)
-->
