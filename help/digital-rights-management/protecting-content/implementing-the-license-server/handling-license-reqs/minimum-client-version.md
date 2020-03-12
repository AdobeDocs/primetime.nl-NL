---
seo-title: Minimale clientversie
title: Minimale clientversie
uuid: f2b56cff-96fa-4954-a08a-9b3e78f496d6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Minimale clientversie {#minimum-client-version}

Adobe Primetime DRM 2.0.2 en hoger introduceren enkele nieuwe gebruiksregels die niet worden begrepen door Primetime DRM 2.0-clients. Door de minimaal ondersteunde clientversie ( `HandlerConfiguration.setMinSupportedClientVersion()`) in te stellen, kan de licentieserver bepalen hoe oudere clients zich gedragen wanneer ze licenties met deze gebruiksregels tegenkomen. Op basis van deze instelling kan de server aangeven of oudere clients de gebruiksregels die ze niet begrijpen, kunnen negeren of dat oudere clients geen licenties met deze gebruiksregels kunnen gebruiken.

Bijvoorbeeld:

* Als de licentie de vereisten voor apparaatmogelijkheden opgeeft ( [Apparaatmogelijkheden vereist voor het afspelen van beveiligde inhoud](../../../protecting-content/introduction/usage-rules/runtime-application-restrictions/device-capabilities.md)), kunnen Primetime DRM-clients 2.0.2 en hoger deze vereisten afdwingen.
* Als de licentieserver geen inhoud wil afspelen op clients die de vereisten voor apparaatmogelijkheden niet begrijpen, stelt u de minimaal ondersteunde clientversie in op 2 (voor 2.0.2). Hierdoor kan de server geen licenties voor Primetime DRM-clients afgeven vóór 2.0.2. De minimale clientversie wordt ook afgedwongen als de licentie wordt overgedragen van de ene client naar de andere.
* Als de licentieserver oudere clients de mogelijkheid wil geven de vereisten voor apparaatmogelijkheden te negeren, stelt u de minimaal ondersteunde clientversie in op 1 (voor Primetime DRM 2.0). De server geeft vervolgens een licentie aan clientversie 2.0 en hoger. Als de client de licentie upgradet of overbrengt naar een andere client met versie 2.0.2 of hoger, worden de vereisten voor apparaatmogelijkheden in de licentie vervolgens afgedwongen omdat de client die gebruiksregel kan ondersteunen.

