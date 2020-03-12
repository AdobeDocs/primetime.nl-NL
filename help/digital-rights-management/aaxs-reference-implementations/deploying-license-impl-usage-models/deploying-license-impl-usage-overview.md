---
seo-title: Overzicht van gebruiksmodellen implementeren
title: Overzicht van gebruiksmodellen implementeren
uuid: 1041bb84-9996-4284-b2a0-d6fc6d4b73d9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Overzicht van gebruiksmodellen implementeren {#implementing-the-usage-models-overview}

De implementatie van de Referentie omvat bedrijfslogica voor het aantonen van hoe te om de volgende vier verschillende gebruiksmodellen voor een stuk verpakte inhoud toe te laten:

* Download-to-own (DTO)
* Huur/Video-op-aanvraag (VOD)
* Abonnement (alles-u-kan-eet)
* Door ad-financiering

Om de demo van het gebruiksmodel toe te laten, specificeer het douanebezit `RI_UsageModelDemo=true` in verpakkingstijd. Als u inhoud verpakt met het opdrachtregelprogramma Media Packager, geeft u het volgende op:

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Als u de optionele demo-modus niet activeert tijdens het verpakken, gebruikt de licentieserver het beleid dat tijdens het verpakken is opgegeven om een licentie uit te geven. Als er meerdere beleidsregels zijn opgegeven, gebruikt de licentieserver het eerste geldige beleid.

In de demo, controleert de bedrijfslogica op de server de daadwerkelijke attributen van de geproduceerde vergunningen. Op het moment van het verpakken moet er alleen minimale beleidsinformatie in de inhoud worden opgenomen. Specifiek, moet het beleid slechts erop wijzen of de authentificatie wordt vereist om tot de inhoud toegang te hebben. Om alle vier gebruiksmodellen toe te laten, omvat één beleid dat anonieme toegang (voor het Adf-gefinancierde model) en één beleid toestaat dat gebruikersnaam/wachtwoordauthentificatie (voor de andere 3 gebruiksmodellen) vereist. Bij het aanvragen van een licentie kan een clienttoepassing bepalen of de gebruiker wordt gevraagd om verificatie op basis van de verificatiegegevens in het beleid.

Om het gebruiksmodel te bepalen waaronder een bepaalde gebruiker een licentie moet krijgen, kunnen vermeldingen worden toegevoegd aan de database van de referentieimplementatie. De `Customer` tabel bevat gebruikersnamen en wachtwoorden voor het verifiëren van gebruikers. Ook wordt aangegeven of de gebruiker een abonnement heeft. Gebruikers met abonnementen krijgen licenties toegewezen volgens het *abonnementsmodel* . Om een gebruiker toegang onder de *Download aan het gebruiksmodellen van het Gebruik van het Gebruik van het Eigen* of van de *Video op bestelling* te verlenen, kan een ingang aan de `CustomerAuthorization` lijst worden toegevoegd, die elk stuk van inhoud specificeert de gebruiker wordt toegestaan om tot en het gebruiksmodel toegang te hebben. Zie het [!DNL PopulateSampleDB.sql] script voor meer informatie over het vullen van elke tabel.

Wanneer een gebruiker een licentie aanvraagt, controleert de server van de Referentie-implementatie de metagegevens die door de client zijn verzonden om te bepalen of de inhoud met de `RI_UsageModelDemo` eigenschap in een pakket is geplaatst. In dat geval worden de volgende bedrijfsregels gebruikt:

* Als een van de beleidsregels verificatie vereist:

   * Als het verzoek een geldig authentificatietoken bevat, zoek de gebruiker in de de gegevensbestandlijst van de Klant. Als de gebruiker is gevonden:

      * Als het `Customer.IsSubscriber` bezit is `true`, produceer een vergunning voor het het gebruiksmodel van het *Abonnement* en verzend het naar de gebruiker.

      * Zoek naar een verslag in de `CustomerAuthorization` gegevensbestandlijst voor deze gebruiker en inhoudsidentiteitskaart Als een record is gevonden:

         * Als `CustomerAuthorization.UsageType` dit het geval is, genereert u een licentie voor het `DTO`gebruiksmodel Downloaden naar eigen ** gebruik en stuurt u deze naar de gebruiker.

         * Als `CustomerAuthorization.UsageType` dit zo is, genereert u een licentie voor het `VOD`gebruiksmodel Video On Demand ** en stuurt u deze naar de gebruiker.
   * Als geen van de beleidsregels anonieme toegang toestaat:

      * Als er geen geldig authentificatietoken in het verzoek is, keer een &quot;vereiste authentificatie&quot;fout terug.
      * Retourneer anders een fout &quot;niet geautoriseerd&quot;.


* Als een van de beleidsregels anonieme toegang toestaat, genereert u een licentie voor het gebruiksmodel met advertenties en stuurt u deze naar de gebruiker.

Voordat de server voor Reference Implementation licenties kan uitgeven voor de gebruiksmodeldemo, moet de server worden geconfigureerd om op te geven hoe licenties worden gegenereerd voor elk van de vier gebruiksmodellen. Dit wordt gedaan door een beleid voor elk gebruiksmodel te specificeren. De implementatie van de Verwijzing omvat vier steekproefbeleid ( [!DNL dto-policy.pol], [!DNL vod-policy.pol], [!DNL sub-policy.pol], [!DNL ad-policy.pol]) of u kunt uw eigen beleid vervangen. In [!DNL flashaccess-refimpl.properties], plaats de volgende eigenschappen om het beleid te specificeren voor elk gebruiksmodel te gebruiken en de beleidsdossiers in de folder te plaatsen die door het `config.resourcesDirectory` bezit wordt gespecificeerd:

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

