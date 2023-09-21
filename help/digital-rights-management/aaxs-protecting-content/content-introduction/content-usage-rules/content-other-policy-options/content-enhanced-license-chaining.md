---
title: Verbeterde licentietakken
description: Verbeterde licentietakken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Verbeterde licentietakken {#enhanced-license-chaining}

Hiermee kan een licentie worden bijgewerkt met behulp van een bovenliggende hoofdlicentie voor het bijwerken van batches van licenties.

De Toegang 2.0 van de Adobe gesteunde vergunning het ketenen waarin zowel de blad als wortelvergunningen aan een specifieke machine worden gebonden. Toegang 3.0 van de Adobe, heeft steun voor verbeterde vergunning het ketenen, waarin een blad aan een wortelvergunning wordt gebonden, en slechts is de wortelvergunning gebonden aan een specifiek machine of domein. De verbeterde licentieketting ondersteunt het insluiten van bladlicenties met de inhoud en de client hoeft alleen de hoofdlicentie van de licentieserver te verkrijgen om de beveiligde inhoud te kunnen gebruiken.

Om de verbeterde licentieketting in te schakelen, wordt een basiscoderingssleutel toegewezen aan het beleid. De sleutel van de wortelencryptie wordt gebruikt om de bladvergunning cryptografisch aan de wortelvergunning te binden.

>[!NOTE]
>
>De verbeterde licentieketting wordt ondersteund door Adobe Access Client versie 3.0 en hoger. Als een oudere client een licentie aanvraagt voor inhoud die ondersteuning biedt voor de uitgebreide licentieketen, kan de licentieserver nog steeds een licentie aan deze client uitgeven met behulp van een licentieketen die wordt ondersteund door Adobe Access 2.0.

Voorbeeld: gebruik deze optie om gekoppelde licenties bij te werken door één hoofdlicentie te downloaden. Implementeer bijvoorbeeld abonnementsmodellen waarbij inhoud kan worden afgespeeld zolang de gebruiker het abonnement elke maand vernieuwt. Het voordeel van deze benadering is dat gebruikers slechts één licentieverkoop hoeven uit te voeren om al hun abonnementslicenties bij te werken.
