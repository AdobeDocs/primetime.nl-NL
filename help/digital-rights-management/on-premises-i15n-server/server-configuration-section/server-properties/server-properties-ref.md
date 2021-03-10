---
title: Referentie servereigenschappen
description: Referentie servereigenschappen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---


# Referentie servereigenschappen{#server-properties-reference}

<!--<a id="section_EC8810492A454BDBA6013FE376360F4E"></a>-->

## Individualisatieserver

<table id="table_ats_tk2_jr">  
 <thead> 
  <tr> 
   <th class="entry"> Configuratie </th> 
   <th class="entry"> Beschrijving </th> 
   <th class="entry"> Voorbeeld </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> Vervoersreferentie </td> 
   <td>De vervoerreferentie wordt gebruikt om verzoeken te decrypteren die van de cliënt worden ontvangen en de teruggestuurde reacties te ondertekenen. Zorg ervoor dat u het bestand <span class="filepath"> AdobeInitial.properties</span> op de juiste wijze configureert met zowel het pad naar het referentiebestand voor transport als het gecodeerde PKCS12-wachtwoord. </td> 
   <td> 
    <ul id="ul_itx_fl2_jr"> 
     <li id="li_A2E65253F37245268A41E6B9C958C8DF"><span class="codeph"> cert.i15n.transport.file =  </span> [PKCS12-bestand met het certificaat en de sleutel voor Individualization Transport] </li> 
     <li id="li_28CDFC0B3D684795AF4708B6D26DF83F"><span class="codeph"> cert.i15n.transport.password =</span> [Gecodeerd wachtwoord voor PKCS12-bestand] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Individuele CA-referentie </td> 
   <td>De Individualization-server gebruikt de Individualization CA-referentie om de machinecertificaten te ondertekenen die deze uitgeeft. Configureer het bestand <span class="filepath"> AdobeInitial.properties</span> op de juiste wijze met zowel het pad naar het I15N CA-referentiebestand als het gecodeerde PKCS12-wachtwoord. </td> 
   <td> 
    <ul id="ul_xsj_nl2_jr"> 
     <li id="li_5A770D8A482F41A4A9AB63CA52C2EB90"><span class="codeph"> cert.i15n.ica.file =</span> [PKCS12-bestand met het CA-cert en de sleutel voor individualisatie] </li> 
     <li id="li_C3C4A2D9AA2A4F86B6DDCFFD9CB55CBB"><span class="codeph"> cert.i15n.ica.password =</span> [Gecodeerd wachtwoord voor PKCS12-bestand] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Individualisatieserversleutelingsreferentie </td> 
   <td> De Individualisatieserver gebruikt de encryptiereferentie om gevoelige dossiers te coderen die aan de servers van de Individualisering moeten worden overgebracht. Dit cert ondersteunt bijvoorbeeld licentiemigratie en wordt ook gebruikt voor het versleutelen van de DRM-persoonlijke sleutels voor de Individualization-servers. </td> 
   <td> 
    <ul id="ul_nbr_kpd_w5"> 
     <li id="li_4226AD6CC85740669DAF467EFD00BBBE"><span class="codeph"> cert.i15n.decryption.file=i15n_transport.pfx</span> </li> 
     <li id="li_F51BDD94F4724FA58CEF9470B6FEE33B"><span class="codeph"> cert.i15n.decryption.password=password</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Inhoudcache </td> 
   <td>Met deze instellingen bepaalt u de locatie vanwaar de Individualisatieserver inhoud downloadt en waar de inhoud op de schijf in de cache wordt geplaatst. De Individualization-server controleert de inhoudsserver bij het opstarten op nieuwe inhoud en vervolgens op de frequentie/tijd die door deze eigenschappen wordt aangegeven. <p>Voor de On-Premises Server van de Individualisatie, hebben wij een aanvankelijke reeks gegevens van het inhoudsgeheime voorgeheugen omvat. Vergeet niet de <i>CONTENTS</i> van de cachemap (niet de cachemap zelf) te kopiëren naar de geconfigureerde <span class="filepath"> AdobeInitial.properties</span> <span class="codeph"> contentServer.localDirectory</span>-locatie. </p> </td> 
   <td> 
    <ul id="ul_r4n_1r2_jr"> 
     <li id="li_CA5F562577B04B4A9966EF46E039A137"><span class="codeph"> contentServer.localDirectory =</span> [Directory waarin lokale inhoud moet worden opgeslagen (normaal tomcat/temp)] </li> 
     <li id="li_9A78FBD6C54D47708226378340B46E8E"><span class="codeph"> contentServer.server =</span> [Webserver om contact op te nemen met ECI-info (<i>niet ondersteund in deze release</i>)] </li> 
     <li id="li_4E7D7F76085D411688B5003E855F860B"><span class="codeph"> contentServer.timeout =</span> [Time-out voor verbinding, in seconden] </li> 
     <li id="li_4B751F238A1643A7AC730CD9354887B6"><span class="codeph"> contentServer.pollFrequency =</span> [Hoe vaak de server moet worden opiniepeild, in dagen (minimaal 1 dag)] </li> 
     <li id="li_8E23C3C6E7EF46B0AFDD7993DE79F142"><span class="codeph"> contentServer.pollTime =</span> [Tijd van de dag om de server te polen, in minuten sinds middernacht] </li> 
    </ul> <p>Lees de sectie <i>CRL- en ECI-bestanden</i> over het up-to-date houden van de cache. </p> </td> 
  </tr> 
  <tr> 
   <td> Individuele CA CRL </td> 
   <td> <p>Dit CRL-distributiepunt (Certificate Revocation List) is opgenomen in elk machinecertificaat dat door de Individualization-server wordt uitgegeven. Tijdens de validatie van machinecertificaten op de licentieserver wordt de CRL gedownload van het distributiepunt dat in het certificaat wordt vermeld (of van de cache wordt gelezen als deze al is gedownload) en gecontroleerd om te controleren of het certificaat niet is ingetrokken. Het wordt geadviseerd om deze verandering van de serverconfiguratie na het gaan door het proces uit te voeren om de Individualisatie CA CRL te creëren en op te stellen. Start de Individualization-server opnieuw nadat de configuratie is gewijzigd. </p> <p>Als u de URL voor het CRL-distributiepunt wilt instellen, moet u het veld <span class="filepath"> AdobeInitial.properties</span> <span class="codeph"> cert.machine.crldp</span> instellen. </p> </td> 
   <td> 
    <ul id="ul_eq3_lv2_jr"> 
     <li id="li_5E37A9E318D742B6A5E1035120888819"><span class="codeph"> cert.machine.crldp =</span> [CRL-distributiepunt] </li> 
    </ul> <p>Bijvoorbeeld: </p>
    <p> <code>
      cert.machine.crldp__DEV=<span>tps://onprem-individualization.com</span>CRL/onprem-individualization-ca.crl
     </code></p>
     <p>De licentieserver moet deze CRL automatisch downloaden zodra een licentieaanvraag is afgehandeld. </p> <p importance="high">Opmerking: Dit distributiepunt wordt <i>niet</i> gecontroleerd door Primetime DRM voor geldigheid. U moet controleren of deze URL geldig is. Fouten als gevolg van een ongeldige URL worden pas weergegeven wanneer validatiefouten worden weergegeven op de licentieserver. </p> </td> 
  </tr> 
  <tr> 
   <td> Logboekregistratie </td> 
   <td>Configureer <span class="filepath"> AdobeInitial.properties</span> voor registratie zoals nodig. </td> 
   <td> 
    <ul id="ul_j1v_kw2_jr"> 
     <li id="li_B60002B33A3042FCBE1F694454966469"><span class="codeph"> adobe.weblogs.loc =</span> [Map waarin logbestanden worden gemaakt] </li> 
     <li id="li_2DD4406FBBF047589BAAAE1C9082D8B3"><span class="codeph"> log.Level =</span> [Het laagste niveau van logboekberichten die in logboeken kunnen verschijnen  <span class="codeph"> [DEBUG | INFO]</span> ] </li> 
     <li id="li_610FAF239A554CE59DAC455174F0CF0A"><span class="codeph"> log.FileName =</span> [Voorvoegsel voor logbestanden. Datum/tijd en extensie ".log" worden toegevoegd aan de bestandsnaam] </li> 
     <li id="li_1F2913B209BE4A0E8207FAAD052D1764"><span class="codeph"> log.RollInterval =</span> [Specificeert hoe vaak de logboeken worden gewist.] </li> 
     <li id="li_3F46C15488114BB5B41035F710E7A19F"><span class="codeph"> log.RollSize =</span> [Rol de logboeken wanneer zij deze grootte bereiken (De logboeken zullen rollen wanneer of  <span class="codeph"> </span> RollIntervalor  <span class="codeph"> </span> RollSizeis bereikt, welke eerst komt)] </li> 
     <li id="li_DA32E862F7B0413885DA20633B682484"><span class="codeph"> log.ReportLogging.Enabled =</span>[ [true] | false ] Geeft aan of een afzonderlijk bestand moet worden gegenereerd dat gegevens bevat die door Adobe worden gebruikt om Individualisatierapporten te genereren.] </li> 
     <li id="li_465CC6D81B8A484CBF4E7A39F7AF86AA"><span class="codeph"> log.ReportLogging.FileName =</span> [Voorvoegsel voor rapportlogbestanden. Datum/tijd en <span class="filepath"> .log</span> uitbreiding zullen aan filename worden toegevoegd. De eigenschap l<span class="codeph"> og.Level</span> is niet van toepassing op dit logbestand, maar <span class="codeph"> log.RollInterval</span> en <span class="codeph"> log.RollSize</span> do.] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Overige </td> 
   <td></td> 
   <td> 
    <ul id="ul_b3b_g1f_jr"> 
     <li id="li_FACF07CB332D416E91FD34DE48152FAA"><span class="codeph"> deviceinfo.key =</span> [Gecodeerde sleutel Base64 die aan HMAC apparateninfo wordt gebruikt alvorens het in het machinetoken te omvatten. De sleutel kan voor de Dev/Staging/Productomgevingen verschillend zijn, maar moet voor alle servers in een bepaalde milieu het zelfde zijn. ] </li> 
     <li id="li_B19C77FD6F91496294DBF836A1922EE1"><span class="codeph"> keys.kgs.server =</span> [Locatie van Key Gen Server (één host/poort die een pool van sleutelservers vertegenwoordigt) ] </li> 
     <li id="li_5DA3C89770804B148EF6FAF01A5AD958"><span class="codeph"> keys.MinQueueSize =</span> [Fetch een andere batch sleutels van de KGS wanneer er nog zoveel toetsen in de wachtrij staan] </li> 
     <li id="li_0C2E5F2FDB824182A6BE418B041D2F28"><span class="codeph"> status.Timeout =</span> [De pagina van de Status zal KGS pingelen om te bepalen of het de server kan bereiken. Het zal tijd uit als een reactie niet terug in de gespecificeerde hoeveelheid tijd wordt ontvangen.] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Server {#section_37FA8EEBA258461F8CFA3ADF37714577} voor sleutelgeneratie

<table id="table_ats_tk2_js"> 
 <thead> 
  <tr> 
   <th class="entry"> Configuratie </th> 
   <th class="entry"> Beschrijving </th> 
   <th class="entry"> Voorbeeld </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> Sleutelgeneratie </td> 
   <td></td> 
   <td> 
    <ul id="ul_nlj_ydf_jr"> 
     <li id="li_E4347D572F004BF0B237A662BFE7F3ED"><span class="codeph"> kgs.Threads =</span> [Aantal threads dat moet worden gebruikt om toetsen te genereren (moet gelijk zijn aan het aantal processors dat beschikbaar is op de computer)] </li> 
     <li id="li_EDBC2535D48E4A66AEB240DB337187FC"><span class="codeph"> kgs.BatchSize =</span> [Aantal sleutels te produceren per partij] </li> 
     <li id="li_07B41546D94F42349103BF8AF4605E14"><span class="codeph"> kgs.KeyDirectory =</span> [Directory waarin belangrijke batchbestanden moeten worden opgeslagen] </li> 
     <li id="li_F4962C97DC3D491DA7FAC826E38A4459"><span class="codeph"> kgs.MaxQueueSize =</span> [Maximumaantal te genereren sleutelbatchbestanden] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Logboekregistratie </td> 
   <td></td> 
   <td> 
    <ul id="ul_kwq_12f_jr"> 
     <li id="li_5E5D34FE5EB44BB898090494C7DDEBD8"><span class="codeph"> adobe.weblogs.loc =</span> [Map waarin logbestanden worden gemaakt] </li> 
     <li id="li_0E34CD32CD5E47729B69B50414F93678"><span class="codeph"> log.FileName =</span> [Voorvoegsel voor logbestanden. Datum/tijd en <span class="filepath"> .log</span> extensie worden toegevoegd aan de bestandsnaam] </li> 
     <li id="li_8AB15ACEC39041A2A04C7301154C6EDB"><span class="codeph"> log.Level =</span> [Het laagste niveau van logboekberichten die in de logboeken kunnen verschijnen] </li> 
     <li id="li_A17E84DA3ED243F381FF3A6184A3CAA0"><span class="codeph"> log.RollInterval =</span> [Specificeert hoe vaak de logboeken worden gewist.] </li> 
     <li id="li_C2B3D111608945DA9D1428BE98D61664"><span class="codeph"> log.RollSize =</span> [Rol de logboeken wanneer zij deze grootte bereiken (De logboeken zullen rollen wanneer of  <span class="codeph"> </span> RollIntervalor  <span class="codeph"> </span> RollSizeis bereikt, welke eerst komt)] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
