---
title: IQ van account wordt gestart met IQ van account, voorwaarden en onboarding
description: 'Hoe kan ik aan boord gaan, voorwaarden en aan de slag gaan met de account-IQ. '
source-git-commit: 258ce10297aa15086a3ed1c1a825af2a30d34d24
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Aan de slag met de IQ van de account {#onboarding}

Lees verder om te weten wat de eerste vereisten zijn voor het gebruik van Account IQ en hoe kan uw bedrijf aan boord gaan om te kijken naar de account delende scores van abonnees.

## Vereisten {#prerequisites}

* De organisatie moet zijn geregistreerd in [!DNL Adobe Marketing Cloud] organisaties.

* Gebruikers in die organisatie moeten worden toegewezen aan het TVE-dashboard Read-Write of het TVE-dashboard Alleen-lezen.

### Voorwaarden voor browsers {#browser-prerequisites}

De account-IQ is een gehoste webservice. Deze is compatibel met de meest recente versie van de volgende browsers:

* Google Chrome
* Mozilla Firefox
* Safari-versie

### Hoe kan ik aan boord gaan van organisaties op account-IQ? {#steps-to-onboard}


Dat is wat we op dit moment hebben. Het is de bedoeling om de dma_primetime controle af te schaffen en een speciaal profiel voor AIQ te hebben. De gebruikers die toegang tot de console moeten hebben zouden dat gebruikersprofiel nodig hebben. Dat is op dit moment echter nog niet gebeurd.

1. Ze hebben hun organisatie op de markt gebracht in Adobe Marketing Cloud @Eric of @Peter, kan je dit nemen.  Ik denk dat het nu &quot;Experience Cloud&quot; heet, maar dat is niet zo belangrijk.  Zijn er meer details? Wordt dit beheerd door een andere groep? Zo ja, kunnen we dan een link, contact, enz. geven? Dit zou ook een voorbehoud moeten bevatten over het controleren of hun org reeds deel van Experience Cloud uitmaakt.

2. Profielen &#39;TVE Dashboard Read-Write&#39; of &#39;TVE Dashboard Read Only&#39; zijn toegewezen aan hun gebruikers in http://adminconsole.adobe.com/.
@Eric, weet je hoe je dit moet doen?  Zijn er substappen?  Kunnen we klanten uitleggen waarom ze alleen-lezen of alleen-lezen hadden gekozen?
@Cristina, kan je een korte verklaring geven dat dit een tijdelijke aanpak is en misschien hoe het zal werken in de volgende versie?

3. Zijn er een proces dat we kunnen opzetten om dit te beheren, omdat hun org-id aan AIQ zijde @Cristina is gewhitelisterd?  Stuur bijvoorbeeld een e-mail naar &quot;DL-AdobePass-Eng AdobePass-Eng@adobe.com&quot; met de org-id van de org, enz.

<!-- these user groups set dma_primetime product context for the user accounts. In AIQ code we’re checking for this product context when providing access. Internally, in the code we have an additional condition: the org id should be whitelisted in order for the users to get access to their data. -->

Wanneer u het dashboard Enterprise van Adobe opent, ziet u de twee nieuwe gebruikersgroepen in uw Adobe Marketing Cloud-organisatie:

TVE-dashboard lezen-schrijven - de leden van deze groep hebben volledige rechten voor alle bewerkbare gedeelten van het dashboard TVE Dashboard Alleen-lezen - de leden van deze groep hebben alleen weergaverechten voor het hele dashboard. Voeg uw account toe aan de TVE Dashboard Read-Write gebruikersgroep, in het Adobe Enterprise Dashboard en meld u vervolgens aan in het Adobe Primetime TVE-dashboard.  Daarna kunt u gebruikersmachtigingen in het dashboard voor Adobe Enterprise beheren door gebruikers toe te voegen aan en te verwijderen uit de twee hierboven vermelde gebruikersgroepen.

...........

In de documentatie die u hebt verstrekt, staat dit onderdeel &quot;Aan de slag met de Gebruiksvoorziening voor het Primetime TVE-dashboard&quot;, dat van toepassing is op de Adobe Pass-console, maar dat ook voor AIQ hetzelfde moet zijn.
http://tve.helpdocsonline.com/primetime-tve-dashboard-user-guide De org die geïnteresseerd is in AIQ moet een organisatie zijn die is geregistreerd in Adobe Marketing Cloud Orgs. Gebruikers in die org moeten worden toegewezen aan het TVE-dashboard Read-Write of het TVE Dashboard Read-Only.
Alleen voor zover u weet, stellen deze gebruikersgroepen de dma_primetime-productcontext voor de gebruikersaccounts in. In de AIQ-code controleren we op deze productcontext wanneer we toegang verlenen. Intern hebben we in de code een extra voorwaarde: de org-id moet worden gewhitelliseerd zodat de gebruikers toegang krijgen tot hun gegevens.
Dat is wat we op dit moment hebben. Het is de bedoeling om de dma_primetime controle af te schaffen en een speciaal profiel voor AIQ te hebben. De gebruikers die toegang tot de console moeten hebben zouden dat gebruikersprofiel nodig hebben. Dat is op dit moment echter nog niet gebeurd.

..........................

1. Ze hebben hun org aan boord in Adobe Marketing Cloud
2. Profielen &#39;TVE Dashboard Read-Write&#39; of &#39;TVE Dashboard Read Only&#39; zijn toegewezen aan hun gebruikers in http://adminconsole.adobe.com/.
3. hun org-id aan AIQ-zijde laten zweven
