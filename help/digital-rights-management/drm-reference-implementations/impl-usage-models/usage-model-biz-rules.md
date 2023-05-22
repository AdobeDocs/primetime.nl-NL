---
title: Gebruikersmodel demo bedrijfsregels
description: Gebruikersmodel demo bedrijfsregels
copied-description: true
exl-id: 689a0335-55e9-427a-bc27-3a69e37ef0b5
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Gebruikersmodel demo bedrijfsregels{#usage-model-demo-business-rules}

Wanneer een gebruiker een licentie aanvraagt, controleert de server voor referentieimplementatie de metagegevens die de client heeft verzonden om te bepalen of de inhoud is verpakt met de `RI_UsageModelDemo` eigenschap. Als dat het geval is, past de server de volgende bedrijfsregels toe.

* Als een van de DRM-beleidsregels verificatie vereist:

   * Als het verzoek een geldig authentificatietoken bevat, onderzoek naar de naam van de gebruiker in de de gegevensbestandlijst van de Klant.

      Als u de naam van de gebruiker niet kunt vinden, voltooi de volgende taken:

      * Als de `Customer.IsSubscriber` eigenschap is ingesteld op `true`, moet u een licentie voor de *`Subscription`* -gebruiksmodel en deze naar de gebruiker sturen.

      * Een record zoeken in het dialoogvenster `CustomerAuthorization` databasetabel voor de naam van de gebruiker en de inhoud-id.

      Als u de record van de gebruiker kunt vinden, voert u de volgende taken uit:

      * Als de `CustomerAuthorization.UsageType` eigenschap is ingesteld op `DTO`, genereert u een licentie voor het DTO-gebruiksmodel en verzendt u deze naar de gebruiker.

      * Als de `CustomerAuthorization.UsageType` eigenschap is ingesteld op `VOD`, genereert u een licentie voor het VOD-gebruiksmodel en verzendt u deze naar de gebruiker.

      Als geen van de DRM-beleidsregels anonieme toegang toestaat, voert u de volgende taken uit:

      * Als er geen geldig authentificatietoken in het verzoek is, moet u een &quot;vereiste authentificatie&quot;fout terugkeren.
      * Retourneer anders een fout &quot;niet geautoriseerd&quot;.



* Als een van de DRM-beleidsregels anonieme toegang toestaat, genereert u een licentie voor het door advertenties gefinancierde gebruiksmodel en stuurt u deze naar de gebruiker.
