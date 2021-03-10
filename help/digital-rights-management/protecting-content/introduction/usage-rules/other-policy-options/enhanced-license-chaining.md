---
title: Verbeterde licentietakken
description: Verbeterde licentietakken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Verbeterde licentietakken {#enhanced-license-chaining}

U kunt de uitgebreide licentieketting gebruiken om een licentie bij te werken door een bovenliggende hoofdlicentie te gebruiken voor het batchgewijs bijwerken van licenties.

Primetime DRM 2.0 ondersteunt licentietekeningen waarin zowel de leaf- als de hoofdlicenties zijn gebonden aan een specifieke computer. Primetime DRM 3.0 en hoger biedt ondersteuning voor uitgebreide licentietekeningen, waarbij een blad is gebonden aan een hoofdlicentie en alleen de hoofdlicentie is gebonden aan een specifieke computer of een specifiek domein. De verbeterde licentieketting ondersteunt het insluiten van een bladlicentie met de inhoud en de client hoeft alleen de hoofdlicentie van de licentieserver te verkrijgen om de beveiligde inhoud te kunnen gebruiken.

Als u uitgebreide licentietekeningen wilt inschakelen, moet u een hoofdcoderingssleutel toewijzen aan een Primetime DRM-beleid. De sleutel van de wortelencryptie wordt gebruikt om de bladvergunning cryptografisch aan de wortelvergunning te binden.

>[!NOTE]
>
>Verbeterde licentieketting wordt ondersteund door Primetime DRM-clients versie 3.0 of hoger. Als een oudere client een licentie aanvraagt voor inhoud die ondersteuning biedt voor de uitgebreide licentieketen, kan de licentieserver nog steeds een licentie aan deze client uitgeven met behulp van de licentieketen die wordt ondersteund door Primetime DRM 2.0.

Voorbeeld van gebruik: Met deze optie kunt u gekoppelde licenties bijwerken door één hoofdlicentie te downloaden. Implementeer bijvoorbeeld abonnementsmodellen waarbij inhoud kan worden afgespeeld zolang de gebruiker het abonnement elke maand vernieuwt. Het voordeel van deze aanpak is dat gebruikers slechts één licentie hoeven aan te schaffen om al hun abonnementslicenties bij te werken.
