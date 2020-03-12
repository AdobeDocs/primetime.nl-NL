---
seo-title: Specifieke beveiligingsinformatie van de leverancier
title: Specifieke beveiligingsinformatie van de leverancier
uuid: 23186770-c73a-4802-bc30-fa9e4b47d9ba
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Specifieke beveiligingsinformatie van de leverancier{#vendor-specific-security-information}

Deze sectie bevat beveiligingsinformatie over besturingssystemen en toepassingsservers die in uw Adobe Access-oplossing zijn opgenomen.

Gebruik de koppelingen in deze sectie om leveranciersspecifieke beveiligingsinformatie voor uw besturingssysteem en toepassingsserver te zoeken.

## Beveiligingsgegevens besturingssysteem {#section-B6D9D6CEA7CC42A8A20346600EFB5E4E}

Wanneer het beveiligen van uw werkend systeem, voer zorgvuldig de maatregelen uit die door uw werkend systeemverkoper, met inbegrip van deze worden beschreven:

* Gebruikers, rollen en bevoegdheden definiëren en beheren
* Bewaking van logboeken en audittrails
* Het verwijderen van onnodige diensten en toepassingen
* Back-ups maken van bestanden

Zie de bronnen in deze tabel voor beveiligingsinformatie over besturingssystemen die door Adobe Access worden ondersteund.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-ugl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Besturingssysteem </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beveiligingsbron </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Microsoft® Windows Server® 2008 Enterprise of Standard Edition </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Windows Server 2008 Security Guide</i> </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Red Hat® Enterprise Linux® 5.4, 5.5 en 5.6. </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">Red Hat Enterprise Linux 5 — Beveiligingsgids</i> </p> </td> 
  </tr> 
 </tbody> 
</table>

In de volgende tabel worden enkele mogelijke benaderingen beschreven voor het minimaliseren van beveiligingskwetsbaarheden die in het besturingssysteem worden gevonden.

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-whl-kjz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Item </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Beveiligingspatches </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Er is een verhoogd risico dat een niet-geautoriseerde gebruiker toegang krijgt tot de toepassingsserver als beveiligingspatches en upgrades van leveranciers niet tijdig worden toegepast. Test beveiligingspatches voordat u ze op productieservers toepast. </p> <p class="- topic/p ">Ook kunt u beleidsregels en procedures maken om regelmatig te controleren op patches en deze te installeren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Virusbeveiligingssoftware </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Virusscanners kunnen geïnfecteerde bestanden herkennen door te zoeken naar een handtekening of op ongewoon gedrag te kijken. Scanners bewaren hun virushandtekeningen in een bestand dat meestal op de lokale vaste schijf wordt opgeslagen. Omdat nieuwe virussen vaak worden ontdekt, moet u dit dossier regelmatig bijwerken opdat de virusscanner alle huidige virussen kan identificeren. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Netwerktijdprotocol (NTP) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voor zowel een goede werking als forensische analyse moet u nauwkeurige tijd in Adobe Access-servers en Adobe Access-pakketten bewaren. Gebruik een veilige versie van NTP om de tijd op alle systemen te synchroniseren die met Internet worden verbonden. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Beveiligingsgegevens toepassingsserver {#section-EBB4EF371CFF4A848694CC240B23D404}

Wanneer het beveiligen van uw toepassingsserver, moet u de maatregelen uitvoeren die door uw serververkoper, met inbegrip van deze worden beschreven:

* Niet-duidelijke gebruikersnaam beheerder gebruiken
* Onnodige services uitschakelen
* De consolemanager beveiligen
* Beveiligde cookies inschakelen
* Onbenodigde poorten sluiten
* Het beperken van administratieve interfaces door IP adressen of domeinen
* Java™ Security Manager gebruiken

