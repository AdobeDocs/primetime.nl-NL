---
title: Overzicht van Roku SSO
description: Info Roku SSO
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---


# Overzicht van Roku SSO {#overview}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Inleiding {#roku-sso-intro}

In dit document worden de gegevens beschreven die nodig zijn om te profiteren van de Single Sign On-functie op Roku-apparaten. Adobe Primetime-verificatie werkt samen met Roku om de gebruikerservaring bij aanmelding te verbeteren en Single Sign On te vergemakkelijken voor tv-abonnees op overal op tv.

De oplossing is gebaseerd op de Clientless REST API van de authentificatie van Adobe Primetime, zodat zullen de meeste programmeurs hun toepassingen niet hoeven bij te werken om van Enige Sign te profiteren.

## Roku SSO inschakelen {#enable-roku-sso}

Roku SSO wordt toegelaten door gebrek tenzij de programmeur of MVPD verzoek om SSO om worden onbruikbaar gemaakt.

Elke programmeur kan SSO op het platform van Roku voor specifieke integratie toelaten/onbruikbaar maken.

### Wat een programmeur moet doen om Roku SSO te laten werken {#make-roku-sso-work}

Voor de toepassingen van Programmers die REST API op cliëntapparaten uitvoeren, zal Roku SSO zonder enige verandering werken. Het besturingssysteem Roku voegt op elk verzoek twee HTTP-headers toe aan de eindpunten van de Adobe Primetime-verificatie.

Voor de toepassingen die van Programmers een Server aan de oplossing van de Server voor REST api uitvoeren, zou de programmeur het team van Roku moeten contacteren en om een configuratie vragen waar deze twee kopballen naar hun domein op alle api stromen zullen worden verzonden.

Door de gebruiker opgegeven abonnee-id die moet worden gebruikt in plaats van de apparaat-id die door de toepassing wordt doorgegeven om SSO voor alle toepassingen (en voor alle apparaten) te garanderen.

Neem contact op met uw Adobe voor specifieke informatie over de indeling van de benodigde koppen.

### Mogelijke problemen {#possible-issues}

Programmeurs moeten controleren of de implementaties op basis van de huidige REST API zonder client geen belemmering vormen voor Roku&#39;s platform-SSO. Zie hieronder een lijst met mogelijke problemen en hoe deze moeten worden opgelost.

| Probleem | Mogelijke oorzaak | Mogelijke oplossingen | |-|-|-|-| |Geen Roku SSO-header verzonden naar Adobe|HTTP gebruiken in plaats van HTTPS voor oproepen naar Adobe Primetime-verificatiedomeinen|HTTPS gebruiken| |MVPD-logo niet weergegeven/niet bijgewerkt voor SSO-tokens|De interface is afhankelijk van lokale opslag|Toepassingen moeten de interface (en lokale opslag indien nodig) bijwerken na verificatie| |Afmelden geactiveerd op geen AuthZ|Toepassingsontwerp|De toepassing moet worden bijgewerkt om zich nooit achter de schermen af te melden|

## Veelgestelde vragen {#faq}

* **Hoe werkt de SBF?**

   SSO zal over alle toepassingen van de Programmer werken die door de authentificatie van Adobe Primetime op alle apparaten van Roku worden aangedreven verbonden aan de zelfde gebruiker Roku.
Niet zullen alle MVPDs Roku SSO toestaan.

* **Zal er om het even welke verandering in authentificatie TTLs zijn?**

   Het eerste geldige authentificatietoken zal voor het uitvoeren van SSO worden gebruikt en, in dit geval, zullen alle andere toepassingen die door SSO zullen voor authentiek worden verklaard zelfde TTL gebruiken tot het verloopt. Wanneer u dus van de ene toepassing naar de andere navigeert, deelt de tweede toepassing de TTL van de eerste toepassing die wordt geverifieerd.

* **Werkt andere Adobe-functionaliteit zoals voorheen?**

   Alle functionaliteit voor primetime-verificatie werkt zoals voorheen.

* **Is er een opt-in-/opt-outproces van de Programmer die van SSO op het platform Roku profiteert?**

   Dit wordt een configuratiewijziging in het Dashboard van Adobe TVE. Elke programmeur kan SSO op het platform van Roku voor specifieke integratie toelaten/onbruikbaar maken.
