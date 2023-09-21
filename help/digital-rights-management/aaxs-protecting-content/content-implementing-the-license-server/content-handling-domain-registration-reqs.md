---
title: Aanvragen voor domeinregistratie afhandelen
description: Aanvragen voor domeinregistratie afhandelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Aanvragen voor domeinregistratie afhandelen{#handling-domain-registration-requests}

Als de DRM-metagegevens aangeven dat domeinregistratie nodig is om de inhoud af te spelen, moet de clienttoepassing de ActionScript-API van DRMManager.addToDeviceGroup() of de joinLicenseDomain()-API aanroepen. Als de client zich nog niet bij de opgegeven domeinserver heeft geregistreerd (of als de toepassing opnieuw moet deelnemen), wordt een domeinregistratieverzoek verzonden. De domeinserver bepaalt of de cliënt wordt toegelaten om zich bij een domein aan te sluiten en geeft één of meerdere domeingeloofsbrieven aan de cliënt uit.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* Als zowel de client als de server protocol versie 5 ondersteunen, is de aanvraag-URL &quot;Domain Server URL in metadata: + &quot;/flashaccess/domain/v4&quot;. Anders is de aanvraag-URL de domeinserver-URL in metagegevens&quot; + &quot;/flashaccess/domain/v3&quot;

Bij het initialiseren van de `DomainRegistrationHandler`, moet de URL van de domeinserver worden opgegeven. Deze URL wordt opgenomen in de domeintokens die door de handler worden uitgegeven om aan te geven welke domeinserver het token heeft uitgegeven. De URL moet overeenkomen met de URL van de domeinserver die is opgegeven in elk beleid waarvoor domeinregistratie bij de server is vereist.

Om te bepalen of de cliënt zich bij het domein mag aansluiten, kan de server de machine en gebruikersinformatie in het verzoek onderzoeken. Zie [Apparaatid&#39;s gebruiken](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-using-machine-ids.md) voor informatie over hoe te om machines te identificeren en te tellen die tot het domein toetreden. De server kan ook bepalen welk domein de client mag verbinden. Merk op dat een cliënt slechts lid van één domein per domeinserver URL kan zijn. Als de computer al een domeintoken heeft voor de URL van deze domeinserver, bevat de domeinregistratieaanvraag de huidige domeinnaam ( `getRequestDomainName()`). Als u een aanvraag opnieuw wilt indienen, moet de domeinserver de huidige set domeinreferenties voor dit domein retourneren of een fout retourneren (de domeinserver retourneert mogelijk niet de domeinreferenties voor een ander domein).

Als de domeinserver authentificatie vereist om zich bij een domein aan te sluiten, zou het verzoek een authentificatietoken moeten bevatten. Net als bij een licentieaanvraag is voor domeinregistratie mogelijk een gebruikersnaam/wachtwoord of aangepaste verificatie vereist. Zie [Gebruikersverificatie](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-authentication/content-user-authentication.md) voor meer informatie over de verwerking van verificatietokens.

De domeinserver is verantwoordelijk voor het opslaan en beheren van de domeinsleutels die aan elk domein zijn gekoppeld. Wanneer een nieuw zeer belangrijk paar voor een domein (de eerste domeinregistratie voor het domein) moet worden geproduceerd, haal `generateDomainCredential` `(String, int, Principal, Date)`. Deze methode zal een nieuw domein zeer belangrijk paar en domeincertificaat produceren. De domeinserver moet de persoonlijke sleutel en het certificaat opslaan en deze objecten leveren bij de verwerking van volgende aanvragen voor dit domein. Het is ook mogelijk om een nieuw zeer belangrijk paar voor een domein te produceren om over de sleutels te rollen. Wanneer u de toetsen voor een bepaald domein overschrijft, moet u de sleutelversie verhogen in `generateDomainCredential` ook.

Elke volgende keer dat een computer zich registreert bij hetzelfde domein, moeten dezelfde persoonlijke domeinsleutel en hetzelfde certificaat worden gebruikt. Invoeden `addDomainCredential(DomainToken, PrivateKey)` om een bestaande domeinreferentie naar de client te retourneren. Als er meerdere domeinreferenties voor het domein zijn omdat de domeinsleutels zijn gewijzigd, moet de server domeinreferenties opgeven voor de huidige domeinsleutel en alle vorige domeinsleutels, zodat de client licenties kan gebruiken die aan oudere domeinsleutels zijn gebonden. Hierdoor kan een licentie die aan een oud domeintoken is gebonden, naar een nieuw geregistreerde computer worden verplaatst en nog steeds kunnen worden afgespeeld.
