---
title: Gebruikersmodel demo bedrijfsregels
description: Gebruikersmodel demo bedrijfsregels
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# Gebruiksmodel demo bedrijfsregels{#usage-model-demo-business-rules}

Wanneer een gebruiker om een vergunning verzoekt, controleert de server van de Implementatie van de Verwijzing de meta-gegevens die de cliënt heeft verzonden, om te bepalen of de inhoud werd verpakt door het `RI_UsageModelDemo` bezit te gebruiken. Als dat het geval is, past de server de volgende bedrijfsregels toe.

* Als een van de DRM-beleidsregels verificatie vereist:

   * Als het verzoek een geldig authentificatietoken bevat, onderzoek naar de naam van de gebruiker in de de gegevensbestandlijst van de Klant.

      Als u de naam van de gebruiker niet kunt vinden, voltooi de volgende taken:

      * Als de eigenschap `Customer.IsSubscriber` is ingesteld op `true`, moet u een licentie voor het *`Subscription`*-gebruiksmodel genereren en naar de gebruiker verzenden.

      * Zoek naar een verslag in de `CustomerAuthorization` gegevensbestandlijst voor de naam van de gebruiker en inhoudsidentiteitskaart

      Als u de record van de gebruiker kunt vinden, voert u de volgende taken uit:

      * Als `CustomerAuthorization.UsageType` bezit aan `DTO` wordt geplaatst, produceer een vergunning voor het DTO gebruiksmodel en verzend het naar de gebruiker.

      * Als de eigenschap `CustomerAuthorization.UsageType` is ingesteld op `VOD`, genereert u een licentie voor het VOD-gebruiksmodel en verzendt u deze naar de gebruiker.

      Als geen van de DRM-beleidsregels anonieme toegang toestaat, voert u de volgende taken uit:

      * Als er geen geldig authentificatietoken in het verzoek is, moet u een &quot;vereiste authentificatie&quot;fout terugkeren.
      * Retourneer anders een fout &quot;niet geautoriseerd&quot;.



* Als een van de DRM-beleidsregels anonieme toegang toestaat, genereert u een licentie voor het door advertenties gefinancierde gebruiksmodel en stuurt u deze naar de gebruiker.

