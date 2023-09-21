---
title: Overzicht van gebruiksmodellen implementeren
description: Overzicht van gebruiksmodellen implementeren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Overzicht van gebruiksmodellen implementeren {#implementing-the-usage-models-overview}

De implementatie van de Referentie omvat bedrijfslogica voor het aantonen van hoe te om de volgende vier verschillende gebruiksmodellen voor een stuk verpakte inhoud toe te laten:

* Download-to-own (DTO)
* Huur/Video-op-aanvraag (VOD)
* Abonnement (alles-wat-je-kan-eet)
* Door ad-financiering

Om de demonstratie van het gebruiksmodel toe te laten, specificeer het douanebezit `RI_UsageModelDemo=true` op het tijdstip van verpakking. Als u inhoud verpakt met het opdrachtregelprogramma Media Packager, geeft u het volgende op:

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE]
>
>Als u de optionele demo-modus niet activeert tijdens het verpakken, gebruikt de licentieserver het beleid dat tijdens het verpakken is opgegeven om een licentie uit te geven. Als er meerdere beleidsregels zijn opgegeven, gebruikt de licentieserver het eerste geldige beleid.

In de demo, controleert de bedrijfslogica op de server de daadwerkelijke attributen van de geproduceerde vergunningen. Op het moment van het verpakken moet er alleen minimale beleidsinformatie in de inhoud worden opgenomen. Specifiek, moet het beleid slechts erop wijzen of de authentificatie wordt vereist om tot de inhoud toegang te hebben. Om alle vier gebruiksmodellen toe te laten, omvat één beleid dat anonieme toegang (voor het Adf-gefinancierde model) en één beleid toestaat dat gebruikersnaam/wachtwoordauthentificatie (voor de andere 3 gebruiksmodellen) vereist. Bij het aanvragen van een licentie kan een clienttoepassing bepalen of de gebruiker wordt gevraagd om verificatie op basis van de verificatiegegevens in het beleid.

Om het gebruiksmodel te bepalen waaronder een bepaalde gebruiker een licentie moet krijgen, kunnen vermeldingen worden toegevoegd aan de database van de referentieimplementatie. De `Customer` tabel bevat gebruikersnamen en wachtwoorden voor het verifiëren van gebruikers. Ook wordt aangegeven of de gebruiker een abonnement heeft. Gebruikers met abonnementen krijgen licenties toegewezen in het kader van de *Abonnement* gebruiksmodel. Om een gebruiker toegang te verlenen krachtens *Downloaden naar eigen* of *Video op aanvraag* gebruiksmodellen, kan een vermelding worden toegevoegd aan de `CustomerAuthorization` tabel, die elk stuk inhoud aangeeft waartoe de gebruiker toegang heeft en het gebruiksmodel. Zie de [!DNL PopulateSampleDB.sql] voor meer informatie over het vullen van elke tabel.

Wanneer een gebruiker een licentie aanvraagt, controleert de server voor referentieimplementatie de metagegevens die door de client zijn verzonden om te bepalen of de inhoud is verpakt met de `RI_UsageModelDemo` eigenschap. Zo ja, dan worden de volgende bedrijfsregels gebruikt:

* Als een van de beleidsregels verificatie vereist:

   * Als het verzoek een geldig authentificatietoken bevat, zoek de gebruiker in de de gegevensbestandlijst van de Klant. Als de gebruiker is gevonden:

      * Als de `Customer.IsSubscriber` eigenschap is `true`, een licentie genereren voor de *Abonnement* -gebruiksmodel en deze naar de gebruiker sturen.

      * Zoeken naar een record in het dialoogvenster `CustomerAuthorization` databasetabel voor deze gebruiker en inhoud-id. Als een record is gevonden:

         * Indien `CustomerAuthorization.UsageType` is `DTO`, een licentie genereren voor de *Downloaden naar eigen* -gebruiksmodel en deze naar de gebruiker sturen.

         * Indien `CustomerAuthorization.UsageType` is `VOD`, een licentie genereren voor de *Video op aanvraag* -gebruiksmodel en deze naar de gebruiker sturen.

   * Als geen van de beleidsregels anonieme toegang toestaat:

      * Als er geen geldig authentificatietoken in het verzoek is, keer een &quot;vereiste authentificatie&quot;fout terug.
      * Retourneer anders een fout &quot;niet geautoriseerd&quot;.

* Als een van de beleidsregels anonieme toegang toestaat, genereert u een licentie voor het gebruiksmodel met advertenties en stuurt u deze naar de gebruiker.

Voordat de server voor Reference Implementation licenties kan uitgeven voor de demo van het gebruiksmodel, moet de server worden geconfigureerd om op te geven hoe licenties worden gegenereerd voor elk van de vier gebruiksmodellen. Dit wordt gedaan door een beleid voor elk gebruiksmodel te specificeren. De implementatie van de Verwijzing omvat vier steekproefbeleid ( [!DNL dto-policy.pol], [!DNL vod-policy.pol], [!DNL sub-policy.pol], [!DNL ad-policy.pol]) of je kunt je eigen beleid vervangen. In [!DNL flashaccess-refimpl.properties], stelt u de volgende eigenschappen in om het beleid op te geven dat voor elk gebruiksmodel moet worden gebruikt en plaatst de beleidsbestanden in de map die door de `config.resourcesDirectory` eigenschap:

```
# Policy file name for Download To Own usage  
RefImpl.UsageModelDemo.Policy.DTO=dto-policy.pol  
# Policy file name for Rental usage  
RefImpl.UsageModelDemo.Policy.VOD=vod-policy.pol  
# Policy file name for Subscription usage  
RefImpl.UsageModelDemo.Policy.Subscribe=sub-policy.pol  
# Policy file name for Ad Supported (free) usage  
RefImpl.UsageModelDemo.Policy.Free=ad-policy.pol
```
