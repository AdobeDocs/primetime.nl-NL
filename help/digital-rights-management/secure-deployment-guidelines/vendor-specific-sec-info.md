---
description: Besturingssystemen en toepassingsservers worden opgenomen in uw Adobe Primetime DRM-oplossing.
seo-description: Besturingssystemen en toepassingsservers worden opgenomen in uw Adobe Primetime DRM-oplossing.
seo-title: Specifieke beveiligingsinformatie van de leverancier
title: Specifieke beveiligingsinformatie van de leverancier
uuid: 331baa42-5e19-40a5-bc74-0b1a2cb9370e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Specifieke beveiligingsinformatie van de leverancier{#vendor-specific-security-information}

Besturingssystemen en toepassingsservers worden opgenomen in uw Adobe Primetime DRM-oplossing.

Zie De Adobe Primetime DRM Key Server gebruiken voor informatie over leveranciersspecifieke beveiligingsgegevens voor uw besturingssysteem en toepassingsserver.

## Beveiligingsgegevens besturingssysteem {#section_53CAD802FCA54C4D8CE0C4E1B3045E52}

Wanneer u het besturingssysteem beveiligt, moet u de maatregelen implementeren die door de leverancier van het besturingssysteem worden beschreven.

Hieronder volgen enkele maatregelen:

* Gebruikers, rollen en bevoegdheden definiëren en beheren
* Bewaking van logboeken en audittrails
* Het verwijderen van onnodige diensten en toepassingen
* Back-ups maken van bestanden

Hier volgt enkele informatie over de besturingssystemen die worden ondersteund door Adobe Primetime DRM:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ugl_kjz_n4"> 
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

Hier volgt een aantal informatie over manieren om beveiligingskwetsbaarheden in het besturingssysteem tot een minimum te beperken:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_whl_kjz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Item </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Beschrijving </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Beveiligingspatches </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Er is een verhoogd risico dat een onbevoegde gebruiker toegang tot de toepassingsserver zou kunnen krijgen als de patches en upgrades van de verkopersveiligheid niet tijdig worden toegepast. </p> <p>Opmerking:  Zorg ervoor dat u beveiligingspatches test voordat u ze op productieservers toepast. </p> <p class="- topic/p ">U moet beleidsregels en procedures maken om regelmatig te controleren op patches en deze te installeren. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Virusbeveiligingssoftware </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Virusscanners kunnen geïnfecteerde bestanden herkennen door te scannen op een handtekening of ongebruikelijk gedrag. </p> <p>Scanners bewaren hun virushandtekeningen in een bestand dat meestal op de lokale vaste schijf wordt opgeslagen. Er worden vaak nieuwe virussen gedetecteerd, dus u moet ervoor zorgen dat dit bestand regelmatig wordt bijgewerkt. Op deze manier kunnen virusscanners altijd alle huidige virussen herkennen. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Netwerktijdprotocol (NTP) </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Voor een correcte werking en forensische analyse, bewaar nauwkeurige tijd op de servers en de verpakkers van Primetime DRM. Gebruik een veilige versie van NTP om de tijd Primetime DRM op alle systemen te synchroniseren die met Internet worden verbonden. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Beveiligingsgegevens toepassingsserver {#section_22986936F1A547CEAB2D97E9E9D4825C}

Wanneer u uw toepassingsserver beveiligt, moet u de maatregelen implementeren die door uw serverleverancier worden beschreven.

Hieronder volgen enkele maatregelen:

* Niet-duidelijke gebruikersnaam beheerder gebruiken
* Onnodige services uitschakelen
* De consolemanager beveiligen
* Beveiligde cookies inschakelen
* Onbenodigde poorten sluiten
* Het beperken van administratieve interfaces door IP adressen of domeinen
* Java™ Security Manager gebruiken

