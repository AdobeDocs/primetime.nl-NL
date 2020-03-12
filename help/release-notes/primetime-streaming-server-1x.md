---
title: Release van Primetime Streaming Server
seo-title: Primetime Streaming Server 1.x-releases
description: Nieuw in de versies Primetime Streaming Server 1.3 en 1.4.
seo-description: Nieuw in de versies Primetime Streaming Server 1.3 en 1.4.
uuid: be05db6b-713f-4406-940d-9f3a805f967b
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: baec714e-9d41-4e8b-b134-13a736885cbd
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Release van Primetime Streaming Server {#primetime-streaming-server-x-releases}

Nieuw in de versies Primetime Streaming Server 1.3 en 1.4.

## Nieuw in Primetime Streaming Server 1.4 (release december) {#what-s-new-in-primetime-streaming-server-december-release}

**Offline Packager**

* HLS-uitvoerstromen bevatten nu ID3-metagegevens die aanwezig zijn in MPEG-2 TS
* Alleen HLS-audiostreams kunnen nu een gekoppelde statische afbeelding hebben
* Ondersteuning voor het leveren van IV als gebruikersinvoer voor HLS AES-coderingsworkflows
* Ondersteuning voor uitvoer IV naar een bestand wanneer IV wordt gegenereerd door de offlineverpakker
* De Maker van playlist steunt nu het associëren van de AudioGroepen van de MultiTaal en de ondertitelgroepen WebVTT van MultiTaal aan media stromen

**Oorspronkelijke server**

* HLS AES-codering is beschikbaar voor Live- en VOD-workflows. De Oorsprong van Primetime kan enkel in Tijd encryptie HLS AES op inkomende stromen HLS of MP4 dossiers toepassen.
* Het kan JIT HLS AES encryptie ook toepassen wanneer het wordt gebruikt om inkomende stromen HDS in stromen HLS om te zetten.
* Primetime-oorsprong ondersteunt nu SWF-whitelistering voor PHLS-streams. Eerder werd deze alleen ondersteund voor PHDS-streams

**Primetime Live Packager**

* Ondersteuning voor het genereren van HLS AES-128-streams voor invoer-RTMP- en MPEG-2 TS-streams

PHDS/PHLS-certificaten zijn vernieuwd. De nieuwe vervaldatum voor dezelfde datum is 01-10-2016.

### **Opgeloste problemen in versie 1.4**{#bug-fixes-included-in-release}

* PTPUB-282 - HLS vastgestelde-vlakke manifest die door OfflinePackager 1.3.1 wordt gecreeerd heeft geen codec en resolutieinformatie.
* PTPUB-353 - PlayListCreator biedt geen ondersteuning voor het toevoegen van WebVTT-informatie in manifest op setniveau
* PTPUB-583 - Het hulpmiddel PlaylistCreator presteert onverwacht groep URI&#39;s met.
* PTPUB-605 Playlist Creator die geen SUBTITLE Group in elke variantstroom opsomt
* PTPUB-634 - Offline Packager voegt SpliceInsert aan manifest toe.
* PTPUB-635 - Multiple SpliceOut-tags ingevoegd voor single ad cue.

### Bekend probleem in release 1.4 {#known-issue-in-release}

* PTPUB-645 DPISimple-modus wordt geforceerd, zelfs wanneer de DPIScte35-modus is opgegeven wanneer zowel opdrachtregelaanwijzingen als in-stream-cues in de configuratie van offlinepakketten zijn opgenomen

## Nieuw in Primetime Streaming Server 1.3.1 (MEI Release) {#what-s-new-in-primetime-streaming-server-may-release}

Versie 1.3.1 verwijst naar de hotfix. Dankzij de volgende verbeteringen is deze upgrade een aanbevolen upgrade voor klanten omdat deze bestaat uit belangrijke prestatieverbeteringen voor JIT MP4-gebruiksgevallen:

1. Prestatiesfix voor MP4 JIT m3u8-generatie bij oorsprong met DRM inclusief Key Rotation
1. Er is een configuratie &#39;CopyQueryParamToJITFragmentURIs&#39; toegevoegd om queryparameters van JIT-manifestverzoek te kopiëren naar gegenereerde fragment-URI&#39;s voor MP4 JIT-conversie. Raadpleeg de documentatie bij HTTP Origin Server voor voorbeeldgebruik
1. MP4-bestanden zonder extensie toestaan voor JIT-conversie via configuratie/MP4Only-configuratie toegevoegd aan vod.xml

### Opgeloste problemen in versie 1.3.1 {#bug-fixes-included-in-release-1}

* 3759167 - Niet alle cues SCTE35 maken het aan outputmanifest wegens timestamp anomalie terwijl het verpakken. Apply pts_adjustment op SpliceTime in TimeSignal van SpliceInfoSection in SCTE35 bericht.

### Bekende problemen in release 1.3.1 {#known-issues-in-release}

* 3717039 - wanneer de verpakker wordt gevormd om DPI eenvoudige wijzescues te produceren, zou het echt moeten zoeken naar specifieke signaaltypes, zoals splice opnemen of plaatsingskans, en slechts die om te zetten in eenvoudige wijzescues. Het zou andere types van signalen zoals programmabegin, netwerkbegin enz. moeten negeren.

* 3718598 - wanneer de Server van de Oorsprong voor het dienen van beschermde inhoud met toegelaten toegang HSM wordt gevormd de backend LunaSA cliënt doet een frequente communicatie met module HSM

## Nieuw in Primetime Streaming Server 1.3 (APRIL-release) {#what-s-new-in-primetime-streaming-server-april-release}

De Primetime 1.3-release biedt verschillende nieuwe functies voor streaming inhoud, betere bruikbaarheid en beveiliging.

**Primetime streamingserver als een verenigde vorm van Live Packager en de oorspronkelijke server**

Primetime Live Packager en Primetime Origin worden samengebracht om als één component te werken. Deze component kan als Packager of als Origin worden gebruikt of de gecombineerde mogelijkheden gebruiken om een Live Stream in te pakken en te hosten.

Dit biedt een uniforme bestandsinterface voor deze servers, zodat ze eenvoudig op één computer kunnen worden uitgevoerd. Het blijft de flexibiliteit verstrekken die als afzonderlijke Packager of Oorsprong moet worden gevormd.

**Ondersteuning voor bèta-MPEG-DASH**

Primetime Streaming Server ondersteunt MPEG-DASH-pakketten voor Live- en VOD-workflows. De component Live Packager zet ingeschrevene RTMP- of MPEG-2-TS-streams om in de DASH-indeling. De component Origin accepteert een DASH-stroom.

Voor VOD-workflows converteert de component Offline Packager MP4- en TS-elementen naar de indeling MPEG-DASH ISOBFF.

**Live naar VOD-conversie**

Er is nu een nieuwe componentopnameserver beschikbaar die het vastleggen van een live stream en archiveren voor VOD-weergave ondersteunt. De klasse ondersteunt het maken van Full Event Replay en van clips/markeringen voor een deel van de gebeurtenis. Deze kan worden geconfigureerd voor het opnemen van alleen-audio streams, het verwijderen van advertenties of sjablonen in Live-inhoud. De opnameserver werkt met Primetime Streaming Server en met Origins van derden.

**RTMP naar HLS-omzetting in Primetime Live Packager**

De component Primetime Live Packager ondersteunt het maken van HLS-streams uit RTMP-streams. Met deze functie kunt u ook Primetime DRM en Protected Streaming toevoegen aan de HLS-uitvoerstreams.

**Verificatie voor binnenkomende RTMP-streams naar Primetime Live Packager**

Een usermgmt.jar wordt nu geleverd met Primetime Live Packager om toegang met vertrouwde aanmeldingsgegevens te configureren wanneer een RTMP-stream naar Primetime Live Packager wordt verzonden

Nu kunnen de codeermodules worden geconfigureerd om een gebruikersnaam/wachtwoord te gebruiken tijdens het verzenden van streams naar Live Packager.

**PlaylistCreator Tool om manifests op hoofdniveau voor HDS en HLS te maken**

Een nutteloos nut PlaylistCreator.jar is nu beschikbaar met Primetime Offline Packager om topniveaumanifestdossiers voor activa van HDS en van HLS gemakkelijk tot stand te brengen.

**Extra beveiligingsfunctie om een Hardware Security Module in te sluiten**

De Offline Packager van Primetime steunt nu de toegang tot van het Certificaat van de Referentie van Packager en Gemeenschappelijke Sleutels van een Module van de Veiligheid van de Hardware.

Een module van de Veiligheid van de Hardware verstrekt extra bescherming aan deze vertrouwelijke activa.

**Verbeterde prestaties voor VOD-pakketten**

Er zijn verschillende prestatieverbeteringen aangebracht om de pakkettijd voor mezzanine-elementen in de Primetime Offline Packager te verbeteren

**Verbeterde prestaties voor JIT MP4-pakketten**

Verschillende prestatieverbeteringen zijn opgenomen in de JIT-pakketmogelijkheden van Primetime Origin voor het verwerken van gebruikersaanvragen voor een grote bibliotheek met VOD-middelen.

## Adobe Primetime Streaming Server 1.4 {#adobe-primetime-streaming-server}

### Minimale systeemvereisten {#minimum-system-requirements}

**Netwerkvereisten**

* Het netwerk zou Multicast moeten worden toegelaten om stroom MPEG-TS van een codeermodule naar Actieve Packager te verzenden. Live Packager accepteert ook een RTMP-stream van een encoder waarvoor geen multicast-netwerk vereist is.

**Ondersteunde besturingssystemen**

* Linux CentOS 6.3 64-bits

**Hardwarevereisten**

* 3,2 GHz Intel® Pentium® 4-processor (dual Intel Xeon® of sneller aanbevolen)
* 64-bits besturingssystemen: 4 GB RAM (8 GB aanbevolen)
* 1 Gb Ethernet-kaart aanbevolen (meerdere netwerkkaarten en 10 Gb ook ondersteund)
* Schijf:

   * (Schijf-SAS): Minimaal 10 GB met 7.500 rpm
   * (Schijf-SSD): 400 MBps lezen/schrijven
   * (NAS) : 1 GB toegewezen koppeling

**Softwarevereisten**

* Oracle Java JRE 1.7 (Aanbevolen: Sun/Oracle Hotspot (JVM). JDK is vereist voor JConsole-toegang tot de JMX API&#39;s

### Primetime Streaming Server installeren en configureren {#install-and-configure-primetime-streaming-server}

**Streaming server installeren**

1. Download de Java SE- en JDK-software van de [Oracle-site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volg de installatie-instructies.
2. Pak het archiefbestand Adobe Primetime-Streaming Server 1.4 uit `Primetime- StreamingServer-1-4-0-b206-12042014.zip` op uw schijf.

**De Primetime Streaming Server starten**

Als u de streamingserver wilt starten, voert u de volgende opdracht uit vanaf de opdrachtregel in de hoofdmap van de streamingserver:\
`$./pss_start.sh`

**De Primetime Streaming Server configureren als Live Packager of HTTP Origin Server**

Als u de streamingserver wilt configureren als Live Packager of Origin Server, werkt u het configuratiebestand pss.xml bij dat zich in de hoofdmap van de streamingserver in de conf-map bevindt:

```
<Config> 
<!-- Set this false to disable the Origin Component. --> 
<OriginEnabled&gt;true&lt;/OriginEnabled>  
<!-- Set this false to disable the Packager Component. -->  
<PackagerEnabled&gt;true&lt;/PackagerEnabled>
</Config>
```

**De Primetime Streaming Server stoppen**

Als u de streamingserver wilt stoppen, voert u de volgende opdracht uit in de hoofdmap van de streamingserver:\
`$./pss_stop.sh`

**Start de Primetime Streaming Server opnieuw**

Als u de streamingserver opnieuw wilt starten, moet u de streamingserver stoppen en starten.

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**De Primetime Streaming Server verwijderen**

Als u de streamingserver wilt verwijderen, stopt u de streamingserver en verwijdert u de pss-map van de streamingserver in de Primetime-directory

## Werken met Live Packager en Origin Server 1.4 {#working-with-live-packager-and-origin-server}

Deze sectie is van toepassing wanneer Primetime Streaming Server niet wordt gebruikt en in plaats daarvan wordt Primetime Live Packager AND/OR Primetime Origin Server geïmplementeerd

### Minimale systeemvereisten {#minimum-system-requirements-1}

**Netwerkvereisten**

* Het netwerk zou Multicast moeten worden toegelaten om stroom MPEG-TS van een codeermodule naar Actieve Packager te verzenden. Live Packager accepteert ook een RTMP-stream van een encoder waarvoor geen multicast-netwerk vereist is.

**Ondersteunde besturingssystemen**

* Linux CentOS 6.3 64-bits

**Hardwarevereisten**

* 3,2 GHz Intel® Pentium® 4-processor (dual Intel Xeon® of sneller aanbevolen)
* 64-bits besturingssystemen: 4 GB RAM (8 GB aanbevolen)
* 1 Gb Ethernet-kaart aanbevolen (meerdere netwerkkaarten en 10 Gb ook ondersteund)
* Schijf:

   * (Schijf-SAS): Minimaal 10 GB met 7.500 rpm
   * (Schijf-SSD): 400 MBps lezen/schrijven
   * (NAS) : 1 GB toegewezen koppeling

**Softwarevereisten**

* Oracle Java JRE 1.7 (Aanbevolen: Sun/Oracle Hotspot (JVM). JDK is vereist voor JConsole-toegang tot de JMX API&#39;s

De bovenstaande minimale systeemvereisten gelden voor zowel de oorspronkelijke server als Live Packager.

### Live Packager installeren en configureren {#install-and-configure-the-live-packager}

**Live Packager installeren**

1. Download de Java SE- en JDK-software van de [Oracle-site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volg de installatie-instructies.
1. Pak het archiefbestand Adobe Primetime - Live Packager 1.4 uit `Primetime-LivePackager-1-4-0-b206-12042014.zip` op de schijf.

**De HTTP Origin Server installeren**

1. Download de Java JRE- en JDK-software van de [Oracle-site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volg de installatie-instructies.
1. Pak het archiefbestand Adobe Primetime - HTTP Origin Server 1.4 `Primetime-HttpOrigin-1-4-0-b206-12042014.zip`uit op uw schijf.

**Als u Live Packager** wilt starten om het verpakkingshulpprogramma te starten, voert u de volgende opdracht uit in de hoofdmap van de verpakker:\
`$packager_start.sh`

**De HTTP Origin Server starten**

Om de Server van de Oorsprong van HTTP te beginnen, voer het volgende bevel van de bevellijn in de de wortelfolder van de Server van de Oorsprong uit:\
`$./origin_start.sh`

**Live Packager stoppen**

Als u de pakketsoftware wilt stoppen, voert u de volgende opdracht uit vanuit de hoofdmap van de pakketsoftware:\
`$packager_stop.sh`

**De HTTP Origin Server stoppen**

Om de Server van de Oorsprong van HTTP tegen te houden, voer het volgende bevel in de de wortelfolder van de Server van de Oorsprong uit:\
`$./origin_stop.sh`

**Live Packager opnieuw starten**

Als u de pakketsoftware opnieuw wilt starten, moet u de pakketsoftware stoppen en starten.

**Opmerking**: Wanneer de pakketsoftware wordt gestart, wordt geprobeerd de opstartgegevens van het fragmentdoel in de tijdelijke map te initialiseren. Als de laarzentrekkerinformatie bij het fragmentdoel wordt gevonden, impliceert het dat de verpakker opnieuw is begonnen. In geval van opnieuw opstarten wacht de verpakker tot de volgende fragmentgrens en begint het pakket. De verpakker voegt een tussenruimte-item in de laarzentrekker in om aan te geven dat er ontbrekende fragmenten zijn.

**Start de HTTP Origin Server opnieuw**

Als u de HTTP Origin Server opnieuw wilt starten, moet u de HTTP Origin Server stoppen en starten.

**Live Packager configureren**

Het distributiebestand bevat een voorbeeldconfiguratie die kan worden gebruikt voor het testen van de verpakker.

Nadat u het archief Adobe Primetime - Live Packager 1.4 hebt uitgepakt, wijzigt u mappen in de map packager en voert u het script packager_start.sh uit. De steekproefconfiguratie luistert op het multicast adres 239.235.0.3:14000, en stelt de lokale oorsprongserver op haven 8080 in werking. De output wordt gevormd om aan `packager/webroot/_default_/_default_/ directory`te schrijven.

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**De HTTP Origin Server configureren**

Verwijs het Primetime document van de Server die van de Oorsprong van HTTP voor de configuratiedetails hier beschikbaar wordt.

**Live Packager verwijderen**

Als u de pakketsoftware wilt verwijderen, stopt u de pakketsoftware en verwijdert u de pakketmap uit de Primetime-map.

**De HTTP Origin Server verwijderen**

Als u de HTTP Origin Server wilt verwijderen, moet u de HTTP Origin Server stoppen en de HTTP Origin Server-directory httporigin uit de Primetime-map verwijderen.

## Adobe Primetime Offline Packager 1.4 {#adobe-primetime-offline-packager}

### Minimale systeemvereisten {#minimum-system-requirements-2}

**Ondersteunde besturingssystemen**

* Linux CentOS 6.3 64-bits

**Hardwarevereisten**

* 3,2 GHz Intel® Pentium® 4-processor (dual Intel Xeon® of sneller aanbevolen)
* 64-bits besturingssystemen: 4 GB RAM (8 GB aanbevolen)
* 1 Gb Ethernet-kaart aanbevolen (meerdere netwerkkaarten en 10 Gb ook ondersteund)
* Schijf:

   * (Schijf-SAS): Minimaal 10 GB met 7.500 rpm
   * (Schijf-SSD): 400 MBps lezen/schrijven
   * (NAS) : 1 GB toegewezen koppeling

**Softwarevereisten**

* Oracle Java JRE 1.7 of hoger.

### Offline Packager installeren en configureren {#install-and-configure-offline-packager}

Voer de volgende stappen uit om Offline Packager te installeren:

1. Download de Java SE-software van de [Oracle-site](https://www.oracle.com/technetwork/java/javase/downloads/index.html) en volg de installatie-instructies.
1. Pak het archiefbestand Adobe Primetime - Offline Packager 1.4 uit `Primetime- OfflinePackager-1-4-0-b206-12042014.zip`op uw schijf.

Verwijs naar het Voorkeur Offline Packager die - document voor de configuratiedetails beschikbaar [hier](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)wordt begonnen.

## Nuttige bronnen {#helpful-resources}

* Zie de volledige Help-documentatie op de pagina [Adobe Primetime Learn &amp; Support](https://helpx.adobe.com/support/primetime.html) .