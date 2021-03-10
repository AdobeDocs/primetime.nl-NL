---
title: Adobe Primetime Ad Insertion-aankondigingen
description: Aankondigingen over recente persberichten en ander verwant nieuws over Primetime Ad Insertion
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Aankondigingen Ad Insertion in primetime

## Programmatische en foutmeldingen reduceren via time-outs voor ad-resolutie

Gepubliceerd op 1 december 2000

Adobe richt zich op het helpen van onze klanten van de Ad Insertion van Primetime maximaliseren van de monetisering van hun advertentielijst. We besteden bijzondere aandacht aan het verminderen van de complexiteit van het voldoen aan de programmatische vraag, die meer dan driekwart van de Amerikaanse digitale video vertegenwoordigt en volgens eMarketer uitgeeft. Met programmatisch verkopen kunnen uitgevers de vraag naar hun advertentielijst maximaliseren, wat leidt tot hogere vulsnelheden en hogere opbrengsten. Maar het verhoogt ook de blootstelling aan en fouten zoals misvormde VAST reacties, de fouten van HTTP en anderen die tot verloren opbrengst en/of slechte kijkervaringen kunnen leiden.

Een veelvoorkomend probleem is de trage reactie van programmatische partners. Typisch, komen programmatic en transacties in milliseconden voor. Soms kan het echter overdreven veel tijd vergen om op één enkele vraagbron te reageren. Een vertraging van één leverancier kan invloed hebben op het volledige proces voor het afspelen van de advertentie, waardoor er tijdelijke lege schermen voor de viewer ontstaan, niet-gevulde advertentieruimten of, in extreme gevallen, de noodzaak om een videostream opnieuw te starten. Helaas is het een grote uitdaging om langzame vraagbronnen te identificeren en te omzeilen.

Om dit probleem aan te pakken, heeft Adobe nieuwe hulpmiddelen aan Ad Insertion toegevoegd Primetime die klanten toestaan om tijdbeperkingen voor advertentieresolutie te plaatsen. Door het instellen van deze regels worden bronnen met een trage vraag automatisch overgeslagen, zodat de videospelers tijdig een antwoord krijgen. Op deze manier kunnen uitgevers de verstoringen van de vraag door bronnen met een lage vraag aanzienlijk beperken, waardoor ze de vulsnelheden van de voorraad kunnen maximaliseren en een ononderbroken kijkervaring van tv-kwaliteit kunnen bieden.

Als u een time-out voor de resolutie van een advertentie wilt inschakelen in Primetime Ad Insertion, wijzigt u de laarzentrekker-API&#39;s zodat deze de parameter ptadtimeout (duur in milliseconden) bevatten.  Alle advertentieverzoeken die niet vóór de time-outduur zijn voltooid, worden niet gekoppeld (eventuele fallback-advertenties worden verwerkt).