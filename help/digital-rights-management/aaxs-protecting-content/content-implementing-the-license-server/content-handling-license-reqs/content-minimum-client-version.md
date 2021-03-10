---
title: Minimale clientversie
description: Minimale clientversie
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Minimale clientversie {#minimum-client-version}

De Toegang 2.0.2 en hoger van Adobe introduceren sommige nieuwe gebruiksregels, die niet door de cliënten van de Toegang 2.0 van Adobe worden begrepen. Door de minimaal ondersteunde clientversie in te stellen ( `HandlerConfiguration.setMinSupportedClientVersion()`), kan de licentieserver bepalen hoe oudere clients zich gedragen wanneer ze licenties met deze gebruiksregels tegenkomen. Op basis van deze instelling kan de server aangeven of oudere clients de gebruiksregels die ze niet begrijpen, kunnen negeren of dat oudere clients geen licenties met deze gebruiksregels kunnen gebruiken.

Bijvoorbeeld:

* Als de licentie de vereisten voor apparaatmogelijkheden opgeeft ( [Apparaatmogelijkheden vereist voor het afspelen van beveiligde inhoud](../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-device-capabilities.md)), kunnen Adobe Access-clients 2.0.2 en hoger deze vereisten afdwingen.
* Als de licentieserver geen inhoud wil afspelen op clients die de vereisten voor apparaatmogelijkheden niet begrijpen, stelt u de minimaal ondersteunde clientversie in op 2 (voor 2.0.2). Dit zal de server verhinderen vergunningen aan de cliënten van de Toegang van Adobe uit te geven vóór 2.0.2. De minimale clientversie wordt ook afgedwongen als de licentie wordt overgedragen van de ene client naar de andere.
* Als de licentieserver oudere clients toestemming wil geven om de vereisten voor apparaatmogelijkheden te negeren, stelt u de minimaal ondersteunde clientversie in op 1 (voor Adobe Access 2.0). De server geeft een licentie voor elke clientversie 2.0 en hoger. Als de client de licentie upgradet of overbrengt naar een andere client met versie 2.0.2 of hoger, worden de vereisten voor apparaatmogelijkheden in de licentie afgedwongen, aangezien de client nu die gebruiksregel ondersteunt.

