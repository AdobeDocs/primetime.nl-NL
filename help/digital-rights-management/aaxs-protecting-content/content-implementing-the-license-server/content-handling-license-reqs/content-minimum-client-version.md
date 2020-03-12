---
seo-title: Minimale clientversie
title: Minimale clientversie
uuid: 9f39e4e7-64eb-43ea-b194-b744838a411e
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# Minimale clientversie {#minimum-client-version}

Adobe Access 2.0.2 en hoger introduceert enkele nieuwe gebruiksregels die niet worden begrepen door Adobe Access 2.0-clients. Door de minimaal ondersteunde clientversie ( `HandlerConfiguration.setMinSupportedClientVersion()`) in te stellen, kan de licentieserver bepalen hoe oudere clients zich gedragen wanneer ze licenties met deze gebruiksregels tegenkomen. Op basis van deze instelling kan de server aangeven of oudere clients de gebruiksregels die ze niet begrijpen, kunnen negeren of dat oudere clients geen licenties met deze gebruiksregels kunnen gebruiken.

Bijvoorbeeld:

* Als de licentie de vereisten voor apparaatmogelijkheden opgeeft ( [Apparaatmogelijkheden vereist voor het afspelen van beveiligde inhoud](../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-device-capabilities.md)), kunnen Adobe Access-clients 2.0.2 en hoger deze vereisten afdwingen.
* Als de licentieserver geen inhoud wil afspelen op clients die de vereisten voor apparaatmogelijkheden niet begrijpen, stelt u de minimaal ondersteunde clientversie in op 2 (voor 2.0.2). Hierdoor kan de server geen licenties meer afgeven aan Adobe Access-clients vóór 2.0.2. De minimale clientversie wordt ook afgedwongen als de licentie wordt overgedragen van de ene client naar de andere.
* Als de licentieserver oudere clients de mogelijkheid wil geven de vereisten voor apparaatmogelijkheden te negeren, stelt u de minimaal ondersteunde clientversie in op 1 (voor Adobe Access 2.0). De server geeft een licentie voor elke clientversie 2.0 en hoger. Als de client de licentie upgradet of overbrengt naar een andere client met versie 2.0.2 of hoger, worden de vereisten voor apparaatmogelijkheden in de licentie afgedwongen, aangezien de client nu die gebruiksregel ondersteunt.

