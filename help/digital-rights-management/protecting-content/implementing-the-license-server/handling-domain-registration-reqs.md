---
seo-title: Aanvragen voor domeinregistratie afhandelen
title: Aanvragen voor domeinregistratie afhandelen
uuid: d92db6c2-5a16-41ea-a1aa-541c59780678
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Aanvragen voor domeinregistratie afhandelen {#handle-domain-registration-requests}

Als de DRM-metagegevens aangeven dat domeinregistratie nodig is om de inhoud af te spelen, moet de clienttoepassing de `DRMManager.addToDeviceGroup()` ActionScript API of `joinLicenseDomain()` iOS API aanroepen. Als de client zich nog niet bij de opgegeven domeinserver heeft geregistreerd (of als de toepassing opnieuw moet deelnemen), wordt een domeinregistratieverzoek verzonden. De domeinserver bepaalt of de cliënt wordt toegelaten om zich bij een domein aan te sluiten en geeft één of meerdere domeingeloofsbrieven aan de cliënt uit.

* De klasse request handler is `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* De klasse request message is `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* Als zowel de client als server protocol versie 5 ondersteunen, is de aanvraag-URL &quot;Domain Server URL in metadata: + &quot; [!DNL /flashaccess/domain/v4]&quot;. Anders is de aanvraag-URL de domeinserver-URL in metagegevens&quot; + &quot; [!DNL /flashaccess/domain/v3]&quot;

Wanneer u de URL initialiseert `DomainRegistrationHandler`, moet u de domeinserver opgeven. Deze URL wordt dan inbegrepen in de domeintekenen die door de manager worden uitgegeven om aan de domeinserver erop te wijzen dat het teken is uitgegeven. De URL moet overeenkomen met de URL van de domeinserver die is opgegeven in elk DRM-beleid waarvoor domeinregistratie bij de server is vereist.

Om te bepalen of de cliënt zich bij het domein mag aansluiten, kan de server de machine en gebruikersinformatie in het verzoek onderzoeken. De server kan ook bepalen welk domein de client mag verbinden.

>[!NOTE]
>
>Een client kan slechts lid zijn van één domein per domeinserver-URL. Als de computer al een domeintoken heeft voor de URL van deze domeinserver, bevat de domeinregistratieaanvraag de huidige domeinnaam ( `getRequestDomainName()`).

Als u een aanvraag opnieuw wilt indienen, moet de domeinserver de huidige set domeinreferenties voor dit domein retourneren of een fout retourneren. De domeinserver retourneert mogelijk niet de domeinreferenties voor een ander domein.

Zie Apparaatid&#39;s [gebruiken](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#use-machine-identifiers) voor informatie over het identificeren en tellen van machines die het domein verbinden.

Als de domeinserver authentificatie vereist om zich bij een domein aan te sluiten, zou het verzoek een authentificatietoken moeten bevatten. Net als bij een licentieaanvraag is voor domeinregistratie mogelijk een gebruikersnaam/wachtwoord of aangepaste verificatie vereist.

Zie [Gebruikersverificatie](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#user-authentication) voor meer informatie over het beheren van verificatietokens.

De domeinserver is verantwoordelijk voor het opslaan en beheren van de domeinsleutels die aan elk domein zijn gekoppeld. Wanneer een nieuw zeer belangrijk paar voor een domein (de eerste domeinregistratie voor het domein) moet worden geproduceerd, moet u aanhalen `generateDomainCredential(String, int, Principal, Date)`. Deze methode produceert een nieuw domein zeer belangrijk paar en domeincertificaat. De domeinserver moet de persoonlijke sleutel en het certificaat opslaan en deze objecten leveren bij de verwerking van volgende aanvragen voor dit domein. Het is ook mogelijk om een nieuw zeer belangrijk paar voor een domein te produceren om over de sleutels te rollen. Wanneer u over de sleutels voor een bepaald domein rolt, ben zeker om de belangrijkste versie binnen te verhogen `generateDomainCredential`.

Elke volgende keer dat een computer zich registreert bij hetzelfde domein, moet dezelfde persoonlijke domeinsleutel en hetzelfde certificaat worden gebruikt. Roep `addDomainCredential(DomainToken, PrivateKey)` aan om een bestaande domeinreferentie naar de client te retourneren. Als er meerdere domeinreferenties voor het domein zijn omdat de domeinsleutels zijn gewijzigd, moet de server domeinreferenties opgeven voor de huidige domeinsleutel en alle vorige domeinsleutels, zodat de client licenties kan gebruiken die aan oudere domeinsleutels zijn gebonden. Hierdoor kan een licentie die aan een oud domeintoken is gebonden, naar een nieuw geregistreerde computer worden verplaatst en nog steeds kunnen worden afgespeeld.
