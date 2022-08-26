---
title: Overzicht iOS/tvOS SDK
description: 'Overzicht iOS/tvOS SDK '
source-git-commit: 6b9508e56bdaa4876bd0974bf7877fb0c1810919
workflow-type: tm+mt
source-wordcount: '3693'
ht-degree: 0%

---


# Overzicht iOS/tvOS SDK {#iostvos-sdk-overview}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.


</br>


## Inleiding {#intro}

iOS AccessEnabler is een objectief C iOS/tvOS-bibliotheek waarmee mobiele apps Adobe Primetime-verificatie kunnen gebruiken voor de machtigingsservices van TV Anywhere. De uitvoering bestaat uit *AccessEnabler* interface die de API voor machtiging definieert, en de *EntitlementDelegate* en *[EntitlementStatus](#ios%20entitlement%20status)* protocollen die de callbacks beschrijven die de bibliotheek teweegbrengt. De interface samen met het protocol wordt bedoeld onder één gemeenschappelijke naam: de AccessEnabler-bibliotheek.

## iOS- en tvOS-vereisten {#reqs}

Voor de huidige technische vereisten met betrekking tot het iOS- en tvOS-platform en Primetime-verificatie raadpleegt u [Vereisten voor Platform/apparaat/gereedschap](#ios)en raadpleeg de releaseopmerkingen die zijn opgenomen in de SDK-download. In de rest van deze pagina ziet u secties waarin wijzigingen worden vermeld die van toepassing zijn op bepaalde SDK-versies en hoger. Hier volgt bijvoorbeeld een legitieme opmerking met betrekking tot de 1.7.5-SDK:

## Native clientworkflows begrijpen {#flows}

De inheemse cliëntwerkschema&#39;s zijn typisch het zelfde als of zeer gelijkaardig aan die van browser-gebaseerde de authentificatieclients van Primetime. Er zijn echter enkele uitzonderingen, zoals hieronder beschreven.

- [Workflow na initialisatie](#post-init)
- [Generic Initial Authentication Workflow](#generic)
- [Logout-workflow](#logout)


### Workflow na initialisatie {#post-init}

Alle die machtigingswerkschema&#39;s door AccessEnabler worden gesteund veronderstellen dat u eerder hebt geroepen [`setRequestor()`](#setReq) om uw identiteit vast te stellen. U doet deze vraag om uw identiteitskaart van de Aanvrager slechts eenmaal te verstrekken, gewoonlijk tijdens de initialisatie/opstellingsfase van uw toepassing.


Met een eigen iOS-client, na uw eerste oproep aan [`setRequestor()`](#setReq)hebt u een keuze voor de volgende stappen:

- U kunt onmiddellijk beginnen machtigingsvraag te maken en hen toe te laten om stil worden een rij gevormd, indien nodig.

- U kunt een bevestiging ontvangen van het succes/de mislukking van [`setRequestor()`](#setReq) door [`setRequestorComplete()`](#setReqComplete) callback.

- U kunt beide bovenstaande handelingen uitvoeren.

U kunt kiezen of uw app wacht op een melding van het succes van [`setRequestor()`](#setReq) of het hebben baseert zich op het mechanisme van de vraagrij van AccessEnabler. Aangezien alle volgende autorisatie- en verificatieverzoeken de aanvrager-id en de bijbehorende configuratiegegevens nodig hebben, [`setRequestor()`](#setReq) de methode blokkeert effectief alle authentificatie en vergunning API vraag tot de initialisering volledig is.

 

### Generic Initial Authentication Workflow {#generic}

Het doel van deze workflow is om een gebruiker aan te melden bij zijn MVPD. Na een geslaagde aanmelding geeft de server de gebruiker een verificatietoken uit. Terwijl de authentificatie typisch als deel van het vergunningsproces wordt gedaan, beschrijft het volgende hoe de authentificatie afzonderlijk kan werken, en omvat geen toestemmingsstappen.

Hoewel deze workflow voor native clients verschilt van de typische browsergebaseerde verificatieworkflow, zijn de stappen 1-5 hetzelfde voor zowel native clients als op browsers gebaseerde clients.

1. Uw toepassing stelt het authentificatiewerkschema met een vraag aan AccessEnabler in werking `getAuthentication() `API-methode, die controleert of een geldig verificatietoken in de cache aanwezig is.
1. Als de gebruiker momenteel voor authentiek wordt verklaard, roept AccessEnabler uw [`setAuthenticationStatus()`](#setAuthNStatus) callback functie, die een authentificatiestatus overgaat die op succes wijst, en de stroom beëindigt.
1. Als de gebruiker momenteel niet voor authentiek wordt verklaard, gaat AccessEnabler de authentificatiestroom door te bepalen of de laatste authentificatiepoging van de gebruiker met bepaalde MVPD succesvol was. Als een MVPD-id in de cache is geplaatst EN de `canAuthenticate` markering is waar OF er is een MVPD geselecteerd met [`setSelectedProvider()`](#setSelProv)wordt de gebruiker niet gevraagd het dialoogvenster MVPD-selectie te openen. De authentificatiestroom gaat verder gebruikend de caching waarde van MVPD (namelijk zelfde MVPD die tijdens de laatste succesvolle authentificatie werd gebruikt). Een netwerkvraag wordt gemaakt aan de backendserver, en de gebruiker wordt opnieuw gericht aan de MVPD login pagina (Stap 6 hieronder).
1. Als er geen MVPD-id in de cache is opgeslagen en er geen MVPD is geselecteerd met [`setSelectedProvider()`](#setSelProv) OF de `canAuthenticate` markering is ingesteld op false, de [`displayProviderDialog()`](#dispProvDialog) callback wordt opgeroepen. Deze callback draagt uw toepassing op om tot UI te leiden die de gebruiker een lijst van MVPDs voorstelt om te kiezen van. Er wordt een array met MVPD-objecten geleverd, die de benodigde informatie bevat om de MVPD-kiezer te maken. Elk MVPD-object beschrijft een MVPD-entiteit en bevat informatie zoals de id van de MVPD (bijv. XFINITY, AT\&amp;T, enz.) en de URL waar het MVPD-logo kan worden gevonden.
1. Zodra een bepaalde MVPD wordt geselecteerd, moet uw toepassing AccessEnabler van de keus van de gebruiker op de hoogte brengen. Zodra de gebruiker gewenste MVPD selecteert, informeert u AccessEnabler van de gebruikersselectie via een vraag aan [`setSelectedProvider()`](#setSelProv) methode.
1. De iOS AccessEnabler roept uw `navigateToUrl:` callback of `navigateToUrl:useSVC:` callback om de gebruiker aan de MVPD login pagina opnieuw te richten. Door één van beide teweeg te brengen, vraagt AccessEnabler aan uw toepassing om tot een `UIWebView/WKWebView or SFSafariViewController` en om URL te laden die in callback wordt verstrekt `url` parameter. Dit is URL van het authentificatieeindpunt op de backendserver. Voor tvOS AccessEnabler worden [status()](#status_callback_implementation) callback wordt aangeroepen met een `statusDictionary` parameter en de opiniepeiling voor de tweede het schermauthentificatie is onmiddellijk begonnen. De `statusDictionary` bevat de `registration code` die moet worden gebruikt voor de tweede schermverificatie. 
1. In het geval van iOS AccessEnabler landt de gebruiker op de aanmeldingspagina van de MVPD om zijn gegevens in te voeren via het medium van uw toepassing `UIWebView/WKWebView or SFSafariViewController `controller. Houd er rekening mee dat tijdens deze overdracht verschillende omleidingsbewerkingen plaatsvinden en dat uw toepassing de URL&#39;s moet controleren die door de controller worden geladen tijdens de meervoudige omleidingsbewerkingen.
1. In het geval van iOS AccessEnabler, wanneer `UIWebView/WKWebView or SFSafariViewController` de controller laadt een specifieke aangepaste URL die uw toepassing moet sluiten en AccessEnabler moet aanroepen `handleExternalURL:url `API-methode. Deze specifieke aangepaste URL is in feite ongeldig en is niet bestemd voor de controller om deze daadwerkelijk te laden. Het moet door uw toepassing slechts als signaal worden geïnterpreteerd dat de authentificatiestroom heeft voltooid en dat het veilig is om het `UIWebView/WKWebView or SFSafariViewController` controller. Als uw toepassing een `SFSafariViewController `de specifieke aangepaste URL wordt gedefinieerd door de `application's custom scheme` (bv.: `adbe.u-XFXJeTSDuJiIQs0HVRAg://adobe.com`), anders wordt deze specifieke aangepaste URL gedefinieerd door de `ADOBEPASS_REDIRECT_URL` constante (d.w.z. `adobepass://ios.app`).
1. Nadat de toepassing is gesloten, worden de `UIWebView/WKWebView or SFSafariViewController` controlemechanisme en roept AccessEnabler `handleExternalURL:url `API methode, terugwint AccessEnabler het authentificatietoken van de backendserver en deelt uw toepassing mee dat de authentificatiestroom volledig is. AccessEnabler roept de [`setAuthenticationStatus()`](#setAuthNStatus) callback met statuscode 1, die op succes wijst. Als er een fout optreedt tijdens het uitvoeren van deze stappen, [`setAuthenticationStatus()`](#setAuthNStatus) callback wordt teweeggebracht met een statuscode van 0, die op authentificatiemislukking, evenals een overeenkomstige foutencode wijst.


>[!WARNING]
>
> Tijdens de stappen waar AccessEnabler controle aan uw app opgeeft (d.w.z., wanneer het de dialoogvakje van de leveranciersselectie wordt getoond, of wanneer UIWebView/WKWebView of SFSafariViewController wordt getoond) heeft de gebruiker de kans om de authentificatiestroom te annuleren. In deze situaties is uw toepassing verantwoordelijk voor het informeren van de AccessEnabler over deze gebeurtenis en het aanroepen van de [`setSelectedProvider()`](#setSelProv) API-methode, null doorgeven als parameter. Dit geeft AccessEnabler een kans om zijn interne staat op te schonen en de authentificatiestroom terug te stellen. Op tvOS kunt u dezelfde methode gebruiken om de verificatieopiniepeiling te annuleren.


### Logout-workflow {#logout}

Voor native clients wordt afmelding op dezelfde manier afgehandeld als het hierboven beschreven verificatieproces.

1. Uw toepassing stelt het logout werkschema met een vraag aan AccessEnabler in werking `logout() `API-methode. De logout is het resultaat van een reeks HTTP omleidingsverrichtingen toe te schrijven aan het feit dat de gebruiker uit zowel de servers van de Authentificatie Primetime als van de servers van MVPD moet worden geregistreerd. Omdat deze stroom niet met een eenvoudig HTTP- verzoek kan worden voltooid dat door de bibliotheek AccessEnabler wordt uitgegeven, een `UIWebView/WKWebView or SFSafariViewController` controller moet worden geïnstantieerd om de HTTP-omleidingsbewerkingen te kunnen volgen.

1. Een patroon gelijkend op de authentificatiestroom wordt gebruikt. De iOS AccessEnabler activeert de `navigateToUrl:` callback of de `navigateToUrl:useSVC:` om een `UIWebView/WKWebView or SFSafariViewController` en om URL te laden die in callback wordt verstrekt `url` parameter. Dit is URL van het logout eindpunt op de achtergrondserver. Voor de tvOS AccessEnabler geldt dat `navigateToUrl:` callback of de `navigateToUrl:useSVC:` callback wordt opgeroepen.

1. Aangezien het door verscheidene omleidingen gaat, moet uw toepassing de activiteit van controleren `UIWebView/WKWebView or SFSafariViewController `en detecteert het moment waarop een specifieke aangepaste URL wordt geladen. Deze specifieke aangepaste URL is in feite ongeldig en is niet bestemd voor de controller om deze daadwerkelijk te laden. Het moet door uw toepassing slechts als signaal worden geïnterpreteerd dat de logout stroom heeft voltooid en dat het veilig is om het controlemechanisme te sluiten. Wanneer de controller deze specifieke aangepaste URL laadt, moet uw toepassing de controller sluiten en AccessEnabler oproepen `handleExternalURL:url `API-methode. Als uw toepassing een `SFSafariViewController `de specifieke aangepaste URL wordt gedefinieerd door de `application's custom scheme` (bijvoorbeeld`adbe.u-XFXJeTSDuJiIQs0HVRAg://adobe.com`), anders wordt deze specifieke aangepaste URL gedefinieerd door de ` ADOBEPASS_REDIRECT_URL  `constante (d.w.z. `adobepass://ios.app`).

1. Uiteindelijk zal AccessEnabler het [`setAuthenticationStatus()`](#setAuthNStatus) callback met een statuscode van 0, die op succes van de logout stroom wijst.

De logout stroom verschilt van de authentificatiestroom in die zin dat de gebruiker niet wordt vereist om met interactie aan te gaan `UIWebView/WKWebView or SFSafariViewController`  op welke manier dan ook. Daarom adviseert Adobe dat u de controle onzichtbaar maakt (d.w.z. verborgen) tijdens het logout-proces.

## Tokens {#tokens}

- [Definities en gebruik](#definitions)
- [Richtlijnen voor caching](#caching)
- [Persistentie](#persistence)
- [Indeling](#format)
- [Apparaatbinding](#device_binding)


### Definities en gebruik {#definitions}

De Primetime oplossing van de authentificatierechten draait rond de generatie van specifieke stukken gegevens (tokens) die de authentificatie Primetime op de succesvolle voltooiing van de authentificatie en vergunningswerkschema&#39;s produceert. Deze tokens worden lokaal opgeslagen op het iOS-apparaat van de client.

 

Tokens hebben een beperkte levensduur; na afloop moeten tokens opnieuw worden uitgegeven door de verificatie- en/of vergunningswerkstromen opnieuw te starten.

 

Er zijn drie typen tokens die worden uitgegeven tijdens de workflows voor machtigingen:

- **Verificatietoken:** Het eindresultaat van het werkschema van de gebruikersauthentificatie zal een authentificatie GUID zijn die AccessEnabler kan gebruiken om vergunningsvragen namens de gebruiker te maken. Deze authentificatie GUID zal een bijbehorende tijd-aan-levende (TTL) waarde hebben die van de authentificatiesessie van de gebruiker zelf kan verschillend zijn. Een authentificatietoken zal worden geproduceerd door authentificatie GUID aan het apparaat te binden dat de authentificatieverzoeken in werking stelt.
- **Token voor autorisatie:** Verleent toegang tot een specifiek beschermd middel dat door unieke resourceID wordt geïdentificeerd. Het bestaat uit een door de vergunningverlenende partij afgegeven autorisatiesubsidie samen met de oorspronkelijke resourceID. Deze informatie is gebonden aan het apparaat dat het verzoek initieert.
- **Kortstondig media-token:** AccessEnabler verleent toegang tot de ontvangende toepassing voor een bepaalde middel door een kort-levend media teken terug te keren. Dit token wordt gegenereerd op basis van het machtigingstoken dat eerder werd verworven voor die specifieke resource. Dit token is niet gebonden aan het apparaat en de bijbehorende levensduur is aanzienlijk korter (standaard: 5 minuten).

Na succesvolle authentificatie en vergunning, zal de authentificatie van Primetime authentificatie authentificatie, vergunning en kortstondige media tokens uitgeven. Deze tokens zouden op het apparaat van de gebruiker moeten worden in het voorgeheugen ondergebracht en voor de duur van hun bijbehorende leven-spanwijdten worden gebruikt.

 

### Richtlijnen voor caching {#caching}

- Verificatietoken
- Token voor autorisatie
- Token voor kortlevende media


#### Verificatietoken

- **AccessEnabler 1.7:** Deze SDK introduceert een nieuwe methode van symbolische opslag, toelatend veelvoudige programmer-MVPD emmers, en daarom, veelvoudige authentificatietokens. Nu, wordt de zelfde opslaglay-out gebruikt voor zowel het &quot;Authentificatie per Vraag&quot;scenario als voor de normale authentificatiestroom. Het enige verschil tussen beide is in de manier de authentificatie wordt uitgevoerd: De &quot;Authentificatie per Aanvrager&quot;bevat een nieuwe verbetering (Passieve Authentificatie) die het voor AccessEnabler mogelijk maakt om backchannel authentificatie uit te voeren, die op het bestaan van een authentificatietoken in de opslag (voor een verschillende Programmer) wordt gebaseerd. De gebruiker hoeft slechts eenmaal te verifiëren en deze sessie wordt gebruikt om verificatietokens te verkrijgen in aanvullende apps. Deze backkanaalstroom vindt plaats tijdens [`setRequestor()`](#setReq) en is meestal transparant voor de programmeur. **Er is echter één belangrijke eis: De programmeur MOET setRequestor() aanroepen vanuit de belangrijkste UI-thread.**
- **AccessEnabler 1.6 en ouder:** De manier waarop verificatietokens in het cachegeheugen worden geplaatst, is afhankelijk van &quot;**Verificatie per aanvrager&quot;** vlag verbonden aan de huidige MVPD:

<!-- end list -->

1. Als de functie &#39;Verificatie per aanvrager&#39; is uitgeschakeld, wordt één verificatietoken lokaal opgeslagen op het algemene plakbord. dit teken zal tussen alle toepassingen worden gedeeld die met huidige MVPD geïntegreerd zijn.
1. Als de eigenschap &quot;Authentificatie per Aanvrager&quot;wordt toegelaten, dan zal een teken uitdrukkelijk met de Programmer worden geassocieerd die de authentificatiestroom uitvoerde (het teken zal niet in het globale plakbord, maar in een privé dossier worden opgeslagen dat slechts aan de toepassing van die Programmer zichtbaar is). In het bijzonder wordt Single Sign-On (SSO) tussen verschillende toepassingen uitgeschakeld. de gebruiker zal de authentificatiestroom uitdrukkelijk moeten uitvoeren wanneer het schakelen naar een nieuwe app (op voorwaarde dat Programmer van tweede app met huidige MVPD wordt geïntegreerd en dat geen authentificatietoken voor die Programmer in het lokale geheime voorgeheugen bestaat).

 

#### Token voor autorisatie

Op om het even welk bepaald ogenblik wordt slechts ÉÉN toestemmingstoken PER BRON caching door AccessEnabler. Er kunnen meerdere machtigingstokens in de cache zijn opgeslagen, maar deze zijn gekoppeld aan verschillende bronnen. Wanneer een nieuw machtigingstoken wordt uitgegeven en er al een bestaat voor *dezelfde resource*, overschrijft het nieuwe token de bestaande waarde in de cache.

 

#### Mediumtoken

De media-token voor korte tijd mag NIET in de cache worden opgeslagen. Het mediatoken moet van de server worden opgehaald telkens wanneer een autorisatie-API wordt aangeroepen, omdat dit beperkt is tot eenmalig gebruik.

 

### Persistentie {#persistence}

Tokens moeten blijvend zijn in opeenvolgende uitvoeringen van dezelfde toepassing. Dit betekent dat zodra de verificatie- en autorisatietokens zijn verkregen en de gebruiker de toepassing sluit, dezelfde tokens beschikbaar zijn voor de toepassing wanneer de gebruiker de toepassing opnieuw opent. Bovendien is het wenselijk dat deze tokens voor meerdere toepassingen blijvend zijn. Met andere woorden, nadat een gebruiker een toepassing gebruikt om zich aan te melden bij een specifieke identiteitsprovider (met succes authentificatie en toestemmingstkens), kunnen de zelfde tokens door een verschillende toepassing worden gebruikt, en de gebruiker wordt niet meer veroorzaakt voor geloofsbrieven wanneer het registreren via de zelfde identiteitsleverancier. Dit type naadloze verificatie-/autorisatieworkflow maakt van de Primetime-verificatieoplossing een echte implementatie op tv en overal. 

 

## iOS

De iOS AccessEnabler-bibliotheek werkt aan de oplossing van de problemen bij het delen van toepassingsgegevens door de tokengegevens op te slaan in een gegevensstructuur die vergelijkbaar is met het klembord, de zogenaamde *plakbord*. Dit systeem-vlakke gedeelde middel verstrekt de belangrijkste ingrediënten die de implementatie van de gewenste blijvende tokens gebruiksgeval toelaten:

- **Ondersteuning voor gestructureerde opslag** - Het plakbord is niet alleen een eenvoudige, lineaire bufferachtige geheugenstructuur. Het verstrekt een woordenboekachtig opslagmechanisme dat voor gegevens het indexeren op user-specified zeer belangrijke waarden toestaat.
- **Ondersteuning voor gegevenspersistentie met behulp van het onderliggende bestandssysteem** - De inhoud van de plakbordstructuur kan als blijvend worden gemarkeerd. In dat geval worden de gegevens opgeslagen in het interne geheugen van het apparaat.

 

Zodra een bepaald teken in het symbolische geheime voorgeheugen wordt geplaatst, zal zijn geldigheid op verschillende tijden door de bibliotheek AccessEnabler worden gecontroleerd.  Een geldig token wordt gedefinieerd als:

- De TTL van het token is niet verlopen.
- De uitgever van het token is opgenomen in de lijst van toegestane identiteitsproviders.

 

## tvOS

Aangezien het plakbord op tvOS niet beschikbaar is, gebruikt de bibliotheek tvOS AccessEnabler de NsUserDefaults als opslagoptie. Dit lost het probleem van het voortbestaan authentificatie en toestemmingstkens op maar de opgeslagen informatie kan niet onder verschillende toepassingen worden gedeeld.

 

**iOS 10 Pasteboard-wijzigingen -** Wanneer u een upgrade uitvoert vanaf een eerdere versie van iOS, wordt het plakbord gewist. Dit betekent dat alle toepassingen opnieuw moeten worden geverifieerd.

 

**iOS 7 Pasteboard-wijzigingen -** Als gevolg van wijzigingen in de werking van plakborden op iOS 7, is de Cross SSO beperkt tussen toepassingen die op iOS 7 worden uitgevoerd. Toepassingen die dezelfde `<Bundle Seed ID>`(ook bekend als `<Team ID>`) deelt tokens, wat betekent dat apps A1 en A2 van dezelfde programmeur X tokens delen, terwijl app A1 (programmeur X) en app A3 (programmeur Y) geen tokens delen. 

- Bundlebron-id/team-id is hetzelfde tussen twee apps als deze worden gegenereerd door hetzelfde inrichtingsprofiel. Meer informatie vindt u op deze link:
   [http://developer.apple.com/library/ios/\#documentation/general/conceptual/DevPedia-CocoaCore/AppID.html ](http://developer.apple.com/library/ios/#documentation/general/conceptual/DevPedia-CocoaCore/AppID.html)
- Deze &quot;Cross SSO&quot;-beperking is aanwezig in iOS 7, ongeacht de gebruikte Primetime-verificatie-SDK. 

Lees deze technische notitie voor meer informatie over het configureren van SSO op iOS 7 en hoger (de technische notitie is van toepassing op Access Enabler v1.8 en hoger): <https://tve.zendesk.com/entries/58233434-Configuring-Pay-TV-pass-SSO-on-iOS>

 

### Token Storage (AccessEnabler 1.7)

Beginnend met AccessEnabler 1.7, kan de symbolische opslag veelvoudige combinaties programmmer-MVPD steunen, die zich op een op meerdere niveaus genestelde kaartstructuur baseren die veelvoudige authentificatietokens kan houden. Deze nieuwe opslag heeft op geen enkele wijze invloed op de openbare API van AccessEnabler en vereist geen wijzigingen aan de kant van de programmeur. Hier volgt een voorbeeld van deze nieuwe functionaliteit:

1. Open App1 (ontwikkeld door Programmer1).
1. Verifieer met MVPD1 (die met Programmer1) geïntegreerd is.
1. Onderbreek of sluit de huidige toepassing en open App2 (ontwikkeld door Programmer2).
1. Laten we ervan uitgaan dat Programmer2 niet geïntegreerd is met MVPD2. Daarom zal de gebruiker NIET in App2 voor authentiek worden verklaard.
1. Verifieer met MVPD2 (die met Programmer2) in App2 geïntegreerd is.
1. De schakelaar terug naar App1; de gebruiker zal nog met Programmer1 voor authentiek worden verklaard.

In oudere versies van AccessEnabler, zou Stap 6 de gebruiker als niet-voor authentiek verklaard teruggeven, omdat de symbolische opslag vroeger slechts één authentificatietoken steunde.

 

Als u zich afmeldt bij een programmeur-/MVPD-sessie, wordt de volledige onderliggende opslag gewist, inclusief alle andere programma-/MVPD-verificatietokens op het apparaat. Anderzijds, annuleert het annuleren van de authentificatiestroom (het aanhalen van [`setSelectedProvider(null)`](#setSelProv)) zal NIET de onderliggende opslag ontruimen, maar het zal slechts het huidige programma/MVPD authentificatiepoging beïnvloeden (door MVPD voor de huidige Programmer te wissen).

 

### Token Importer (AccessEnabler 1.7)

Een andere opslag-verwante eigenschap die in AccessEnabler 1.7 inbegrepen is maakt het mogelijk om authentificatietokens van oudere opslaggebieden in te voeren. Deze &quot;Symbolische Importer&quot;helpt om verenigbaarheid tussen opeenvolgende versies te bereiken AccessEnabler, die de SSO staat handhaven zelfs wanneer de opslagversie wordt bevorderd. De importeur wordt uitgevoerd tijdens de [`setRequestor()`](#setReq) stroom en loopt in de volgende twee scenario&#39;s (veronderstellend dat geen geldig authentificatietoken voor huidige programmeur in de huidige opslag aanwezig is):

- De eerste installatie van een 1.7-app die is ontwikkeld door een specifieke programmeur
- Upgradeweg aan een toekomstige AccessEnabler die een nieuwe opslag gebruikt

De importbewerking is transparant voor de programmeur en vereist geen codewijziging in de clienttoepassing.

 

### Token Sanitizer (AccessEnabler 1.7.5)

Van AccessEnabler 1.7.5 door:sturen, loopt deze dienst op [`setRequestor()`](#setReq)`. `Het is ontwikkeld als resultaat van de iOS 7-switch van het WiFi MAC-adres naar het IDFA voor tracering. De sanitizer zorgt ervoor dat de huidige opslag alleen geldige verificatietokens bevat (geldig in termen van de apparaat-id, eerder berekend met het MAC-adres, vóór iOS7). Met de Token Sanitizer worden alle ongeldige tokens verwijderd. 

 

De Symbolische dienst Sanitizer is het nuttigst wanneer een toepassing AccessEnabler 1.7.5 op iOS 6 wordt gebruikt, en dan de gebruiker werkt aan iOS 7 bij. Als dit gebeurt, zijn alle verificatietokens die zijn verkregen op iOS 6 nu ongeldig (omdat het algoritme voor de apparaat-id is gewijzigd van het gebruik van het MAC-adres in de IDFA). De sanitizer zal alle ongeldige tokens ontruimen, en de gebruiker zal dan unauthenticated zijn. 

 

Zonder de Symbolische Sanitizer die ongeldige tokens verwijdert, zou AccessEnabler geen vergunningen wegens de aanwezigheid van ongeldige authentificatietokens verkrijgen. Dit zou voor de eindgebruiker lastig blijken om te zuiveren, aangezien de berichten van de vergunningsfout cryptisch en niet overdreven nuttig kunnen zijn in het bepalen van wat het probleem veroorzaakte. 

 

### Indeling {#format}

- [AuthN Token](#authn_token)
- [AuthZ Token](#authz_token)
- [Token voor korte media](#short_token)
- [Apparaatbinding](#device_binding)


Merk op dat het formaat van de tokens AuthN en AuthZ hier voor achtergrondinformatie slechts inbegrepen zijn. De structuur van deze tokens kan op elk gewenst moment worden gewijzigd door Primetime-verificatie. Programmeurs hoeven niet de nauwkeurige structuur van de tokens AuthN en AuthZ te kennen om hun apps uit te voeren, aangezien de tokens AuthN en AuthZ niet op het lokale apparaat worden blootgesteld. Het token Short Media *is* aan de toepassing van de programmeur worden blootgesteld.

 

#### Verificatietoken {#authn_token}

Hieronder ziet u de indeling van het verificatietoken:

```
  <signatureInfo>base64(...)<signatureInfo>
  <simpleAuthenticationToken>
      <simpleTokenAuthenticationGuid>71C69B91-F327-F185-F29E-2CE20DC560F5</simpleTokenAuthenticationGuid>
      <simpleTokenRequestorID>TEST_REQUESTOR</simpleTokenRequestorID>
      <simpleTokenDomainName>adobe.com</simpleTokenDomainName>
      <simpleTokenExpires>2011/03/19 02:29:34 GMT +0200</simpleTokenExpires>
      <simpleTokenMsoID>Adobe</simpleTokenMsoID>
      <simpleTokenDeviceID>
          <simpleTokenFingerprint>
              HASH(true device identification info)
          </simpleTokenFingerprint>
      </simpleTokenDeviceID>   
  </simpleAuthenticationToken>
```
 

#### Token voor autorisatie {#authz_token}

De onderstaande lijst geeft de indeling van de machtigingstoken weer:

```
  <signatureInfo>base64(...)<signatureInfo>
  <simpleAuthorizationToken>
      <simpleTokenRequestorID>TEST_REQUESTOR</simpleTokenRequestorID>
      <simpleTokenResourceID>TEST_RESOURCE</simpleTokenResourceID>
      <simpleTokenTTL>2011/03/17 14:40:08 GMT +0200</simpleTokenTTL>
      <simpleTokenMsoID>Adobe</simpleTokenMsoID>
      <simpleTokenDeviceID>
          <simpleTokenFingerprint>
              HASH(true device identification info)
          </simpleTokenFingerprint>
      </simpleTokenDeviceID>
  </simpleAuthorizationToken>
```
 

#### Token voor korte media {#short_token}

Hieronder ziet u de indeling van de token voor korte media. Dit teken wordt blootgesteld aan de toepassing van de Programmer. Het wordt doorgegeven aan de toepassing van de programmeur na een succesvol machtigingsproces:

```
  <signatureInfo>signature<signatureInfo>
  <shortAuthorizationToken>
    <sessionGUID>session_guid</sessionGUID>
    <requestorID>requestor_id</requestorID>
    <resourceID>resource_id</resourceID>
    <ttl>ttl_in_ms</ttl>
    <issueTime>issue_time</issueTime>
    <mvpdId>mvpd_id</mvpdId>
    <proxyMvpdId>proxy_mvpd_id</proxyMvpdId>
  </shortAuthorizationToken>
```
 

### Apparaatbinding {#device_binding}

Let in de bovenstaande XML-items op de tag met de titel `simpleTokenFingerprint`. Het doel van deze tag is om de individualisatiegegevens van de native apparaat-id op te slaan. De bibliotheek AccessEnabler kan dergelijke individualiseringsinformatie verkrijgen en het ter beschikking stellen aan de diensten van de authentificatie Primetime tijdens de machtigingsvraag. De dienst zal deze informatie gebruiken en zal het in de daadwerkelijke tokens inbedden, zo effectief binden de tokens aan een specifiek apparaat. Het uiteindelijke doel hiervan is om de tokens niet-overdraagbaar te maken op verschillende apparaten.

 

Aangezien dit duidelijk een veiligheids verwante eigenschap is, is deze informatie inherent &quot;gevoelig&quot;uit veiligheidsoogpunt. Daarom moet deze informatie worden beschermd tegen knoeien en afluisteren. Het afluisterprobleem wordt opgelost door de verificatie-/autorisatieverzoeken via het HTTPS-protocol te verzenden. De manipulatiebeveiliging wordt afgehandeld door de apparaatidentificatiegegevens digitaal te ondertekenen. De bibliotheek AccessEnabler verwerkt een apparaatidentiteitskaart van informatie die door het apparaat wordt verstrekt, dan verzendt apparatenidentiteitskaart &quot;in duidelijk&quot;naar de servers van de authentificatie Primetime als verzoekparameter. De servers van de authentificatie Primetime ondertekenen digitaal apparatenidentiteitskaart met Adobe privé sleutel en voegen het aan het authentificatietoken toe dat aan AccessEnabler is teruggekeerd. Aldus wordt apparaat-id gebonden aan het verificatietoken. Tijdens de vergunningsstroom, verzendt AccessEnabler opnieuw apparatenidentiteitskaart in duidelijk, samen met het authentificatietoken. Als het validatieproces mislukt, zullen de workflows voor verificatie en autorisatie automatisch mislukken. De servers van de authentificatie Primetime passen de privé sleutel op apparatenidentiteitskaart toe en vergelijken het met de waarde in het authentificatietoken. Als ze niet overeenkomen, mislukt die machtigingsstroom.

 

**Nota over de Binding van het Apparaat in AccessEnabler 1.7.5:** Beginnend met AccessEnabler 1.7.5, is er een verandering in hoe apparatenidentiteitskaart wordt berekend om individualiseringsinformatie voor een apparaat van iOS te verstrekken. Deze wijziging weerspiegelt een wijziging in iOS 7: In iOS 7 biedt Apple het WiFi MAC-adres niet langer als traceringsoptie, ten gunste van de ID (Identifier for Advertisers) ervan. Aangezien de informatie over individualisatie voor een toepassing die op iOS 7 wordt uitgevoerd op IDFA is gebaseerd, en die informatie in de machtigingsstroomtokens wordt ingebed, betekent dit dat er een aantal verschillende mogelijke effecten op gebruikerservaring zijn die uit deze wijziging voortvloeien. De verschillende mogelijke effecten zijn gebaseerd op welke versie van iOS de gebruiker bijwerkt in combinatie met welke versie van AccessEnabler de programmeur bijwerkt. Voor details over deze verandering, zie de nota&#39;s van de Versie inbegrepen met AccessEnabler SDK 1.7.5.


## Gerelateerde informatie {#related}

<!--
- [iOS/tvOS Integration Cookbook](#)
- [iOS/tvOS API Reference](#)
- [Handling MVPDs with 'Not Trusted Certificates' in Primetime
  authentication native SDK (Tech Note)](#)
- [Registering Native Clients](#)
- [Generating Digital Certificates](#)
- [Understanding Tokens](#understanding_tokens)
- [Identifying Protected Resources](#)
- [SSO on iOS when using the Primetime authentication Access
  Enabler](#)
-->
