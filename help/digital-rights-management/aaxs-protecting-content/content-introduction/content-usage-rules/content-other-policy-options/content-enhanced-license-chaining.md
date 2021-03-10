---
title: Verbeterde licentietakken
description: Verbeterde licentietakken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---


# Verbeterde licentietakken {#enhanced-license-chaining}

Hiermee kan een licentie worden bijgewerkt met behulp van een bovenliggende hoofdlicentie voor het bijwerken van batches van licenties.

Adobe Access 2.0 ondersteunde licentieketting waarin zowel de leaf- als de hoofdlicenties zijn gebonden aan een specifieke computer. Adobe Access 3.0 biedt ondersteuning voor uitgebreide licentietekeningen, waarbij een blad is gebonden aan een hoofdlicentie en alleen de hoofdlicentie is gebonden aan een specifieke computer of een specifiek domein. De verbeterde licentieketting ondersteunt het insluiten van bladlicenties met de inhoud en de client hoeft alleen de hoofdlicentie van de licentieserver te verkrijgen om de beveiligde inhoud te kunnen gebruiken.

Om de verbeterde licentieketting in te schakelen, wordt een basiscoderingssleutel toegewezen aan het beleid. De sleutel van de wortelencryptie wordt gebruikt om de bladvergunning cryptografisch aan de wortelvergunning te binden.

>[!NOTE]
>
>De verbeterde licentieketting wordt ondersteund door Adobe Access-clients versie 3.0 en hoger. Als een oudere client een licentie aanvraagt voor inhoud die ondersteuning biedt voor de uitgebreide licentieketen, kan de licentieserver nog steeds een licentie aan deze client uitgeven met behulp van een licentieketen die wordt ondersteund door Adobe Access 2.0.

Voorbeeld van gebruik: Met deze optie kunt u gekoppelde licenties bijwerken door één hoofdlicentie te downloaden. Implementeer bijvoorbeeld abonnementsmodellen waarbij inhoud kan worden afgespeeld zolang de gebruiker het abonnement elke maand vernieuwt. Het voordeel van deze benadering is dat gebruikers slechts één licentieverkoop hoeven uit te voeren om al hun abonnementslicenties bij te werken.
