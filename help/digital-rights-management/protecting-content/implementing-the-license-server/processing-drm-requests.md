---
title: Adobe Primetime DRM-verzoeken verwerken
description: Adobe Primetime DRM-verzoeken verwerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Adobe Primetime DRM-verzoeken verwerken {#process-adobe-primetime-drm-requests}

De algemene benadering van het beheren van verzoeken is een manager te creëren, het verzoek te ontleden, de reactiegegevens of foutencode te plaatsen, en de manager te sluiten.

De basisklasse die wordt gebruikt voor het verwerken van interactie met een enkele aanvraag/reactie is `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Een instantie van de `HandlerConfiguration` wordt gebruikt om de handler te initialiseren. `HandlerConfiguration` slaat de informatie van de serverconfiguratie, met inbegrip van vervoergeloofsbrieven, timestamp tolerantie, de lijsten van de beleidsupdate, en herroepingslijsten op.De manager leest de verzoekgegevens en ontleedt het verzoek in een geval van `RequestMessageBase`. De aanroeper kan de informatie in het verzoek onderzoeken en beslissen of een fout of een succesvolle reactie (subklassen van `RequestMessageBase` een methode opgeven voor het instellen van reactiegegevens).

Als het verzoek succesvol is, plaats de reactiegegevens; anders aanhalen `RequestMessageBase.setErrorData()` bij mislukking. Beëindig altijd de implementatie door het `close()` methode (aanbevolen wordt `close()` worden opgeroepen in het `finally` blok van een `try` instructie). Zie de `MessageHandlerBase` API verwijzingsdocumentatie voor een voorbeeld van hoe te om de manager aan te halen.

>[!NOTE]
>
>HTTP-statuscode 200 (OK) moet worden verzonden als reactie op alle aanvragen die door de handler worden verwerkt. Als de handler niet kon worden gemaakt vanwege een serverfout, reageert de server mogelijk met een andere statuscode, zoals 500 (Interne serverfout).

De client gebruikt de licentieserver-URL die tijdens het verpakken is opgegeven als de basis-URL voor alle aanvragen die naar de licentieserver worden verzonden. Als de server-URL bijvoorbeeld is opgegeven als &lt;[!DNL ht<span></span>tps://licenseserver.com/path]>, verzendt de client vervolgens aanvragen naar &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/.]> Zie de volgende secties voor meer informatie over het specifieke pad dat voor elk type aanvraag wordt gebruikt. Wanneer u uw licentieserver implementeert, moet u ervoor zorgen dat de server reageert op de paden die voor elk type aanvraag zijn vereist.

Een licentieaanvraag kan een verificatietoken bevatten. Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek een `AuthenticationToken` door de `AuthenticationHandler`en de SDK zorgt ervoor dat de token geldig is voordat een licentie wordt uitgegeven.

## Apparaatid&#39;s gebruiken {#use-machine-identifiers}

Alle Adobe Primetime DRM-aanvragen (met uitzondering van aanvragen die FMRMS-compatibiliteit ondersteunen) bevatten informatie over de computertoken die tijdens de individualisatie aan de client is uitgegeven. De machine-token bevat een machine-id. Dit is een id die tijdens de individualisatie is toegewezen. U kunt deze id gebruiken om het aantal machines te tellen waarvan een gebruiker een vergunning heeft gevraagd of zich bij een domein heeft aangesloten.

U kunt een id als volgt gebruiken:

* De `getUniqueId()` de methode keert een koord terug dat aan een apparaat tijdens individualisering is toegewezen. U kunt de tekenreeksen opslaan in een database en zoeken op id. Deze id verandert echter als de gebruiker de vaste schijf opnieuw formatteert en opnieuw individualiseert. Deze id heeft ook een andere waarde voor Adobe AIR en Adobe Flash Player in verschillende browsers op dezelfde computer.
* Als u de machines nauwkeuriger wilt tellen, kunt u `getBytes()` om de volledige id op te slaan. Om te bepalen of de machine eerder is gezien, krijg alle herkenningstekens voor een gebruikersnaam en vraag `matches()` om te controleren of er een overeenkomst is. Omdat de `matches()` moet worden gebruikt om de waarden te vergelijken die door `MachineId.getBytes`Deze optie is echter alleen praktisch als er een klein aantal waarden moet worden vergeleken, bijvoorbeeld de machines die aan een bepaalde gebruiker zijn gekoppeld.

## Gebruikersverificatie {#user-authentication}

Een Adobe Primetime DRM-aanvraag kan een verificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek omvatten `AuthenticationToken` door de `AuthenticationHandler`. Als u tot het token toegang wilt hebben en het wilt verifiëren, moet u `RequestMessageBase.getAuthenticationToken()`. Als u een aanvraag voor een gebruikersnaam/wachtwoord op de client wilt starten, gebruikt u de `DRMManager.authenticate()` ActionScript of iOS API.

Als de client en server een aangepast verificatiemechanisme gebruiken, verkrijgt de client een verificatietoken via een ander kanaal en wordt het aangepaste verificatietoken ingesteld met behulp van het `DRMManager.setAuthenticationToken` ActionScript 3.0 API. Gebruiken `RequestMessageBase.getRawAuthenticationToken()` om het token voor aangepaste verificatie op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.

## Replay-beveiliging {#replay-protection}

Voor afspeelbeveiliging kunt u controleren of de bericht-id onlangs is bekeken door `RequestMessageBase.getMessageId()`. Als dat het geval is, probeert een aanvaller mogelijk het verzoek opnieuw af te spelen. Dit moet worden geweigerd. Om herhalingspogingen te ontdekken, kan de server een lijst van onlangs gezien berichtherkenningstekens opslaan en elk inkomend verzoek tegen de caching lijst controleren. Om de hoeveelheid tijd te beperken moet de berichtherkenningstekens worden opgeslagen, vraag `HandlerConfiguration.setTimestampTolerance()`. Als dit bezit wordt geplaatst, ontkent SDK dan om het even welk verzoek dat een timestamp voor meer dan het gespecificeerde aantal seconden van de servertijd draagt.

## Terugdraaidetectie {#rollback-detection}

Voor terugdraaiopsporing, vereisen sommige gebruiksregels de cliënt om staatsinformatie voor handhaving van de rechten te handhaven. Om bijvoorbeeld de gebruiksregel voor het afspeelvenster af te dwingen, slaat de client de datum en tijd op waarop de gebruiker de inhoud voor het eerst begon te bekijken. Deze gebeurtenis activeert het begin van het afspeelvenster. Als u het afspeelvenster veilig wilt afdwingen, moet de server ervoor zorgen dat de gebruiker geen back-up maakt van de client en deze status herstelt om de begintijd van het afspeelvenster die op de client is opgeslagen, te verwijderen. De server doet dit door de waarde van de terugdraaiteller van de cliënt te volgen.

Voor elk verzoek, krijgt de server de waarde van de teller door te roepen `RequestMessageBase.getClientState()` om de `ClientState` object, vervolgens aanroepen `ClientState.getCounter()` om de huidige waarde van de cliëntstaatsteller te verkrijgen. Deze waarde moet door de server worden opgeslagen voor elke client (gebruik `MachineId.getUniqueId()` om de cliënt te identificeren verbonden aan de het terugschroeven van prijstellwaarde), en dan te roepen `ClientState.incrementCounter()` om de tellerwaarde met één te verhogen. Als de server detecteert dat de tellerwaarde lager is dan de laatste waarde die door de server wordt gezien, is de clientstatus mogelijk teruggedraaid.

Zie de `ClientState` API-naslagdocumentatie voor meer informatie over de detectie van knoeiboel van de clientstatus.

## Algemene serverconfiguratiegegevens{#global-server-configuration-data}

Naast de configuratie die door de licentieserver wordt gebruikt, `HandlerConfiguration` slaat configuratieinformatie op die naar de cliënt kan worden verzonden om te controleren hoe de vergunningen worden afgedwongen. Dit doet u door een `ServerConfigData` klasse en aanroepen `HandlerConfiguration.setServerConfigData()`. Deze instellingen zijn alleen van toepassing op licenties die door deze licentieserver zijn uitgegeven.

De tolerantie van de klokwindback is één bezit dat door de vergunningsserver kan worden geplaatst om te controleren hoe de cliënt vergunningen afdwingt. Standaard kunnen gebruikers de computerklok 4 uur terugzetten zonder licenties ongeldig te maken. Als een licentieserveroperator een andere instelling wil gebruiken, kan de nieuwe waarde worden ingesteld in het dialoogvenster `ServerConfigData` klasse. Wanneer u de waarde van een van deze instellingen wijzigt, moet u het versienummer verhogen door `setVersion()`. De nieuwe waarden worden alleen naar de client verzonden als de versie op de client ouder is dan de huidige versie `ServerConfigData` versie.

## Crossdomain DRM-beleidsbestand {#crossdomain-drm-policy-file}

Als de licentieserver op een ander domein wordt gehost dan de SWF voor het afspelen van video, moet een DRM-beleidsbestand voor meerdere domeinen ( [!DNL crossdomain.xml]) is nodig om de SWF in staat te stellen licenties aan te vragen bij een licentieserver. Een domeinoverschrijdend DRM-beleidsbestand wordt vertegenwoordigd door een XML-bestand waarmee de server kan aangeven dat de gegevens en documenten ervan beschikbaar zijn voor SWF-bestanden die vanuit andere domeinen worden aangeboden. Elk SWF-bestand dat wordt aangeboden vanuit een domein dat is opgegeven in het DRM-beleidsbestand voor meerdere domeinen van de licentieserver, heeft toegang tot gegevens of elementen van die licentieserver.

Adobe raadt ontwikkelaars aan de best practices te volgen bij het implementeren van het bestand met interdomeinbeleid door vertrouwde domeinen alleen toegang te verlenen tot de licentieserver en de toegang tot de submap met licentie op de webserver te beperken.

Raadpleeg de volgende locaties voor meer informatie over domeinoverschrijdende DRM-beleidsbestanden:

* Controlemiddelen voor websites (DRM-beleidsbestanden)
* Specificatie van DRM-beleidsbestand voor meerdere domeinen: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
