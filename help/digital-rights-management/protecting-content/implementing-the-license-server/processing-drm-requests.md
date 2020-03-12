---
seo-title: Adobe Primetime DRM-verzoeken verwerken
title: Adobe Primetime DRM-verzoeken verwerken
uuid: ee10504d-84f0-472a-b58a-2a87fdeedfc1
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Adobe Primetime DRM-verzoeken verwerken {#process-adobe-primetime-drm-requests}

De algemene benadering van het beheren van verzoeken is een manager te creëren, het verzoek te ontleden, de reactiegegevens of foutencode te plaatsen, en de manager te sluiten.

De basisklasse die wordt gebruikt om interactie met één aanvraag/reactie af te handelen, is `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. Er wordt een instantie van de `HandlerConfiguration` klasse gebruikt om de handler te initialiseren. `HandlerConfiguration` slaat de informatie van de serverconfiguratie, met inbegrip van vervoergeloofsbrieven, timestamp tolerantie, de lijsten van de beleidsupdate, en herroepingslijsten op.De manager leest de verzoekgegevens en ontleedt het verzoek in een geval van `RequestMessageBase`. De aanroeper kan de informatie in het verzoek onderzoeken en beslissen of om een fout of een succesvolle reactie (subklassen van verstrekken een methode voor het plaatsen van reactiegegevens) terug te keren. `RequestMessageBase`

Als het verzoek succesvol is, stelt u de reactiegegevens in. anders aanhalen `RequestMessageBase.setErrorData()` bij mislukking. Beëindig altijd de implementatie door de `close()` methode aan te roepen (het wordt geadviseerd dat `close()` wordt geroepen in het `finally` blok van een `try` verklaring). Zie de `MessageHandlerBase` API verwijzingsdocumentatie voor een voorbeeld van hoe te om de manager aan te halen.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>HTTP-statuscode 200 (OK) moet worden verzonden als reactie op alle aanvragen die door de handler worden verwerkt. Als de handler niet kon worden gemaakt vanwege een serverfout, reageert de server mogelijk met een andere statuscode, zoals 500 (Interne serverfout).

De client gebruikt de licentieserver-URL die tijdens het verpakken is opgegeven als de basis-URL voor alle aanvragen die naar de licentieserver worden verzonden. Als de server-URL bijvoorbeeld is opgegeven als &lt;[!DNL ht<span></span>tps://licenseserver.com/path]>, verzendt de client vervolgens aanvragen naar &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/...]> Zie de volgende secties voor meer informatie over het specifieke pad dat voor elk type aanvraag wordt gebruikt. Wanneer u uw licentieserver implementeert, moet u ervoor zorgen dat de server reageert op de paden die voor elk type aanvraag zijn vereist.

Een licentieaanvraag kan een verificatietoken bevatten. Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek een `AuthenticationToken` geproduceerd door het bevatten `AuthenticationHandler`, en SDK zal ervoor zorgen het teken geldig is alvorens een vergunning uit te geven.

## Apparaatid&#39;s gebruiken {#use-machine-identifiers}

Alle Adobe Primetime DRM-aanvragen (met uitzondering van aanvragen die FMRMS-compatibiliteit ondersteunen) bevatten informatie over de computertoken die tijdens de individualisatie aan de client is uitgegeven. De machine-token bevat een machine-id. Dit is een id die tijdens de individualisatie is toegewezen. U kunt deze id gebruiken om het aantal machines te tellen waarvan een gebruiker een vergunning heeft gevraagd of zich bij een domein heeft aangesloten.

U kunt een id als volgt gebruiken:

* De `getUniqueId()` methode keert een koord terug dat aan een apparaat tijdens individualisering is toegewezen. U kunt de tekenreeksen opslaan in een database en zoeken op id. Deze id verandert echter als de gebruiker de vaste schijf opnieuw formatteert en opnieuw individualiseert. Deze id heeft ook een andere waarde voor Adobe AIR en Adobe Flash Player in verschillende browsers op dezelfde computer.
* Als u de machines nauwkeuriger wilt tellen, kunt u gebruiken `getBytes()` om het volledige herkenningsteken op te slaan. Om te bepalen of de machine eerder is gezien, krijg alle herkenningstekens voor een gebruikersnaam en vraag `matches()` om te controleren of om het even welke gelijke. Omdat de `matches()` methode moet worden gebruikt om de waarden te vergelijken die door `MachineId.getBytes`zijn teruggekeerd, is deze optie slechts praktisch wanneer er een klein aantal te vergelijken waarden zijn; bijvoorbeeld de machines die aan een bepaalde gebruiker zijn gekoppeld.

## Gebruikersverificatie {#user-authentication}

Een Adobe Primetime DRM-aanvraag kan een verificatietoken bevatten.

Als gebruikersbenaming/wachtwoordauthentificatie werd gebruikt, kan het verzoek een `AuthenticationToken` geproduceerd door `AuthenticationHandler`. Als u tot het token toegang wilt hebben en het wilt verifiëren, moet u het gebruiken `RequestMessageBase.getAuthenticationToken()`. Gebruik de `DRMManager.authenticate()` ActionScript- of iOS-API om een aanvraag voor een gebruikersnaam/wachtwoord op de client te starten.

Als de client en server gebruikmaken van een aangepast verificatiemechanisme, verkrijgt de client via een ander kanaal een verificatietoken en wordt het aangepaste verificatietoken ingesteld met behulp van de `DRMManager.setAuthenticationToken` ActionScript 3.0-API. Gebruik deze optie `RequestMessageBase.getRawAuthenticationToken()` om het aangepaste verificatietoken op te halen. De serverimplementatie bepaalt of het token voor aangepaste verificatie geldig is.

## Replay-beveiliging {#replay-protection}

Voor de bescherming van het afspelen, kunt u willen controleren of bericht herkenningsteken onlangs door te roepen is gezien `RequestMessageBase.getMessageId()`. Als dat het geval is, probeert een aanvaller mogelijk het verzoek opnieuw af te spelen. Dit moet worden geweigerd. Om herhalingspogingen te ontdekken, kan de server een lijst van onlangs gezien berichtherkenningstekens opslaan en elk inkomend verzoek tegen de caching lijst controleren. Om de hoeveelheid tijd te beperken moet de berichtherkenningstekens worden opgeslagen, vraag `HandlerConfiguration.setTimestampTolerance()`. Als dit bezit wordt geplaatst, ontkent SDK dan om het even welk verzoek dat een timestamp voor meer dan het gespecificeerde aantal seconden van de servertijd draagt.

## Terugdraaidetectie {#rollback-detection}

Voor terugdraaiopsporing, vereisen sommige gebruiksregels de cliënt om staatsinformatie voor handhaving van de rechten te handhaven. Om bijvoorbeeld de gebruiksregel voor het afspeelvenster af te dwingen, slaat de client de datum en tijd op waarop de gebruiker de inhoud voor het eerst begon te bekijken. Deze gebeurtenis activeert het begin van het afspeelvenster. Als u het afspeelvenster veilig wilt afdwingen, moet de server ervoor zorgen dat de gebruiker geen back-up maakt van de client en deze status herstelt om de begintijd van het afspeelvenster die op de client is opgeslagen, te verwijderen. De server doet dit door de waarde van de terugdraaiteller van de cliënt te volgen.

Voor elk verzoek, krijgt de server de waarde van de teller door `RequestMessageBase.getClientState()` te roepen om het `ClientState` voorwerp te verkrijgen, dan roepend `ClientState.getCounter()` om de huidige waarde van de teller van de cliëntstaat te verkrijgen. De server moet deze waarde voor elke client opslaan (gebruik `MachineId.getUniqueId()` om de client te identificeren die is gekoppeld aan de waarde van de terugdraaiteller) en vervolgens aanroepen `ClientState.incrementCounter()` om de tegenwaarde met één te verhogen. Als de server detecteert dat de tellerwaarde lager is dan de laatste waarde die door de server wordt gezien, is de clientstatus mogelijk teruggedraaid.

Zie de `ClientState` API-naslagdocumentatie voor meer informatie over de detectie van knoeiboel van de clientstatus.

## Algemene serverconfiguratiegegevens{#global-server-configuration-data}

Naast configuratie die door de vergunningsserver wordt gebruikt, `HandlerConfiguration` slaat configuratieinformatie op die naar de cliënt kan worden verzonden om te controleren hoe de vergunningen worden afgedwongen. Dit gebeurt door een `ServerConfigData` klasse te maken en aan te roepen `HandlerConfiguration.setServerConfigData()`. Deze instellingen zijn alleen van toepassing op licenties die door deze licentieserver zijn uitgegeven.

De tolerantie van de klokwindback is één bezit dat door de vergunningsserver kan worden geplaatst om te controleren hoe de cliënt vergunningen afdwingt. Standaard kunnen gebruikers de computerklok 4 uur terugzetten zonder licenties ongeldig te maken. Als een licentieserveroperator een andere instelling wil gebruiken, kan de nieuwe waarde in de `ServerConfigData` klasse worden ingesteld. Wanneer u de waarde van om het even welk van deze montages verandert, ben zeker om het versieaantal te verhogen door te roepen `setVersion()`. De nieuwe waarden worden alleen naar de client verzonden als de versie op de client ouder is dan de huidige `ServerConfigData` versie.

## Crossdomain DRM-beleidsbestand {#crossdomain-drm-policy-file}

Als de licentieserver wordt gehost op een ander domein dan het SWF-bestand voor het afspelen van video, is een DRM-beleidsbestand ( [!DNL crossdomain.xml]) voor meerdere domeinen nodig om het SWF-bestand in staat te stellen licenties aan te vragen bij een licentieserver. Een domeinoverschrijdend DRM-beleidsbestand wordt vertegenwoordigd door een XML-bestand waarmee de server kan aangeven dat de gegevens en documenten ervan beschikbaar zijn voor SWF-bestanden die vanuit andere domeinen worden aangeboden. Elk SWF-bestand dat wordt aangeboden vanuit een domein dat is opgegeven in het DRM-beleidsbestand voor meerdere domeinen van de licentieserver, heeft toegang tot gegevens of elementen van die licentieserver.

Adobe raadt ontwikkelaars aan de best practices te volgen bij het implementeren van het bestand met interdomeinbeleid door vertrouwde domeinen alleen toegang te verlenen tot de licentieserver en de toegang tot de submap met licentie op de webserver te beperken.

Raadpleeg de volgende locaties voor meer informatie over domeinoverschrijdende DRM-beleidsbestanden:

* Controlemiddelen voor websites (DRM-beleidsbestanden)
* Specificatie van DRM-beleidsbestand voor meerdere domeinen: [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)