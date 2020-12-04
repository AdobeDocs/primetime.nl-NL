---
description: De PlayReady interface van het licentietoken verleent productie en testdiensten.
seo-description: De PlayReady interface van het licentietoken verleent productie en testdiensten.
seo-title: PlayReady verzoek voor licentietoken/reactie
title: PlayReady verzoek voor licentietoken/reactie
uuid: 20ebd582-ebb9-4716-8c1e-df3e58d6ec14
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 3%

---


# PlayReady-verzoek voor licentietoken / reactie {#playready-license-token-request-response}

De PlayReady interface van het licentietoken verleent productie en testdiensten.

Deze HTTP-aanvraag retourneert een token dat voor een PlayReady-licentie kan worden ingewisseld.

**Methode: GET, POST**  (met een www-url-gecodeerde hoofdtekst die parameters voor beide methoden bevat)

**URL&#39;s:**

* **Productie:** `https://pr-gen.{prod_domain}/hms/pr/token`

* **Testen:** ` [https://pr-gen.test.expressplay.com/hms/pr/token](https://pr-gen.test.expressplay.com/hms/pr/token)`

* **Voorbeeldverzoek:**

   ```
   <xref href="https: pr-gen.test.expressplay.com="" hms="" pr="" token?customerAuthenticator="201722,1ad8eed133edf43cbcc185f0236828ae&kid=b366360da82e9c6e0b0984002a362cf2&contentKey=b366360da82e9c6e0b0984002a362cf2&rightsType=BuyToOwn&analogVideoOPL=0&compressedDigitalAudioOPL=0&compressedDigitalVideoOPL=0&uncompressedDigitalAudioOPL=0&uncompressedDigitalVideoOPL=0&quot; format=&quot;html&quot; scope=&quot;external&quot;">
   https://pr-gen.test.expressplay.com/hms/pr/token?customerAuthenticator=
    <ExpressPlay customer authenticator identifier>
    &kid=<CEKSID>
    &contentKey=<CEK>
    &rightsType=BuyToOwn
    &analogVideoOPL=0
    &compressedDigitalAudioOPL=0
    &compressedDigitalVideoOPL=0
    &uncompressedDigitalAudioOPL=0
    &uncompressedDigitalVideoOPL=0
   </xref href="https:>
   ```

* **Samplereactie:**

   ```
   {"licenseAcquisitionUrl":"https://expressplay-licensing.axprod.net/LicensingService.ashx",
               "token":"<base64-encoded ExpressPlay token>"}
   ```

## Parameters {#section_26F8856641A64A46A3290DBE61ACFAD2} aanvragen

**Tabel 9: Parameters tokenquery**

<table id="table_zxg_dyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Query-parameter</b> </th> 
   <th class="entry"><b>Beschrijving</b> </th> 
   <th class="entry"><b>Vereist?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> customerAuthenticator</span> </td> 
   <td> <p>Dit is de API-sleutel van uw klant, één voor uw productie- en testomgeving. U vindt dit op het tabblad ExpressPlay-beheerdashboard. </p> </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> errorFormat</span> </td> 
   <td>Of <span class="codeph"> html</span> of <span class="codeph"> json</span>. Als <span class="codeph"> html</span> (het gebrek) een vertegenwoordiging van HTML van om het even welke fouten in het entiteitlichaam van de reactie wordt verstrekt. <p>Als <span class="codeph"> json</span> wordt gespecificeerd, is een gestructureerde reactie in formaat JSON teruggekeerd. Zie <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON-fouten</a> voor meer informatie. </p> <p>Het mime-type van de reactie is <span class="codeph"> text/uri-list</span> als de bewerking succesvol is, <span class="codeph"> text/html</span> voor HTML-foutindeling, of <span class="codeph"> application/json</span> voor JSON-foutindeling. </p> </td> 
   <td> Nee </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 10: Parameters licentiequery**

<table id="table_f1l_fyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Query-parameter</b> </th> 
   <th class="entry"><b>Beschrijving</b> </th> 
   <th class="entry"><b>Vereist?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> generalFlags</span> </td> 
   <td>Een hexadecimale tekenreeks van 4 bytes die de licentiemarkeringen vertegenwoordigt. Voor een permanente licentie moet deze worden ingesteld op "0000001". <p>Opmerking: Verhuurlicenties (<span class="codeph"> rightsType=Rental</span>) MOETEN blijvend zijn. </p> </td> 
   <td> Nee </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kek</span> </td> 
   <td> Key Encryption Key (KEK). Toetsen worden gecodeerd met een KEK opgeslagen met behulp van een sleutelomsluitingsalgoritme (AES Key Wrap, RFC3394). </td> 
   <td> Nee </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kind</span> </td> 
   <td>Een hexadecimale tekenreeksrepresentatie van 16 bytes van de coderingssleutel voor inhoud of een tekenreeks <span class="codeph"> ^sommige string'</span>. De lengte van de tekenreeks gevolgd door '^' mag niet groter zijn dan 64 tekens. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> ek</span> </td> 
   <td> Een hexadecimale tekenreeksrepresentatie van de gecodeerde inhoudssleutel. </td> 
   <td> Nee </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> contentKey</span> </td> 
   <td> Een hexadecimale tekenreeksrepresentatie van 16 bytes van de coderingssleutel voor inhoud </td> 
   <td>Ja, tenzij <span class="codeph"> kek</span> en <span class="codeph"> ek</span> of <span class="codeph"> child</span> worden opgegeven </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rightsType</span> </td> 
   <td>Geeft het soort rechten aan. Moet <span class="codeph"> BuyToOwn</span> of <span class="codeph"> Huur</span> zijn. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> huur.periodEndTime</span> </td> 
   <td>Einddatum huur. Deze waarde MOET de notatie "RFC 3339" _ datum/tijd hebben in de notatie "Z"-zoneaanduiding ("Zulu time") of een geheel getal voorafgegaan door een plusteken (+). <p>Als de waarde een <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339</a> datum/tijd formaat is, dan vertegenwoordigt het een absolute vervaldatum/tijd voor de vergunning. Een voorbeeld van een RFC 3339 datum/tijd is 2006-04-14T12:01:10Z. </p> <p> Als de waarde een geheel getal is dat wordt voorafgegaan door een plusteken (+), wordt deze genomen als een relatief aantal seconden vanaf het moment dat het token wordt uitgegeven. De inhoud kan na deze keer niet worden afgespeeld. Alleen geldig als <span class="codeph"> rightsType</span> <span class="codeph"> Rental</span> is. </p> </td> 
   <td>Ja, wanneer <span class="codeph"> rightsType</span> <span class="codeph"> Rental</span> is. </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> huur.playDuration</span> </td> 
   <td>Tijd, in seconden, dat de inhoud kan worden afgespeeld zodra het afspelen is gestart. Alleen geldig als <span class="codeph"> rightsType</span> Huur is. </td> 
   <td> Nee </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> analogVideoOPL</span> </td> 
   <td> Gehele waarde om het niveau van de Bescherming van de Output voor analoge video aan te geven. Geldig bereik 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressedDigitalAudioOPL</span> </td> 
   <td> Gehele waarde om het niveau van de Bescherming van de Output voor gecomprimeerde digitale audio aan te geven. Geldig bereik 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressedDigitalVideoOPL</span> </td> 
   <td> Gehele waarde om het niveau van de Bescherming van de Output voor gecomprimeerde digitale video aan te geven. Geldig bereik 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressedDigitalAudioOPL</span> </td> 
   <td> Gehele waarde om het niveau van de Bescherming van de Output voor ongecomprimeerde digitale audio aan te geven. Geldig bereik 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressedDigitalVideoOPL</span> </td> 
   <td> Gehele waarde om het niveau van de Bescherming van de Output voor ongecomprimeerde digitale video aan te geven. Geldig bereik 0-999. </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> unknownOutputBehavior</span> </td> 
   <td>Vereist gedrag als de uitvoer onbekend is. Toegestane waarden: <span class="codeph"> Allow</span>, <span class="codeph"> Disallow</span> or <span class="codeph"> SDOnly</span> </td> 
   <td> Nee </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> outputControlFlags</span> </td> 
   <td> Een hexadecimale waarde van 4 bytes om de markeringen voor andere uitvoerbesturingselementen aan te geven </td> 
   <td> Nee </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionType</span> </td> 
   <td>Een willekeurig woord van 4 letters dat een 32-bits id voor een extensie vertegenwoordigt. De 8-bits ASCII-code van elke letter is het corresponderende 8-bits bytegedeelte van de id. De id-waarde 0x61626364 (hexadecimaal) wordt bijvoorbeeld geschreven als '<span class="codeph"> abcd</span>', omdat de ASCII-code voor 'a' 0x61 is, enzovoort. </td> 
   <td> Nee </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionPayload</span> </td> 
   <td> Een base64-gecodeerde tekenreeks van de extensie. </td> 
   <td>Ja, wanneer <span class="codeph"> extensionType</span> wordt gespecificeerd. </td> 
  </tr> 
 </tbody> 
</table>

## Reacties {#section_0079C31B4AF14DBBB6277CF251FB90E3}

**Tabel 11: HTTP-reacties**

| **HTTP-statuscode** | **Beschrijving** | **Inhoudstype** | **Entiteitslichaam bevat** |
|---|---|---|---|
| `200 OK` | Geen fout. | `text/uri-list` | Vergunningaankoop-URL en token |
| `400 Bad Request` | Ongeldige args | `text/html` of  `application/json` | Foutbeschrijving |
| `401 Unauthorized` | Auth failed | `text/html` of  `application/json` | Foutbeschrijving |
| `404 Not found` | Ongeldige URL | `text/html` of  `application/json` | Foutbeschrijving |
| `50x Server Error` | Serverfout | `text/html` of  `application/json` | Foutbeschrijving |

**Tabel 12: Gebeurtenisfoutcodes**

<table id="table_lqb_ycs_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>Code</b> </th> 
   <th class="entry"><b>Beschrijving</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> -2002 </td> 
   <td> Ongeldige vervaltijd van token: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2003 </td> 
   <td> Ongeldig IP-adres </td> 
  </tr> 
  <tr> 
   <td> -2005 </td> 
   <td> Ongeldige coderingssleutel voor inhoud: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2008 </td> 
   <td> Ongeldige vlag voor uitvoercontrole opgegeven: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> Verificatietoken moet worden opgegeven </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td>Verificatietoken ongeldig: &lt;details&gt; <p>Opmerking:  Dit kan gebeuren als de authenticator het mis heeft of wanneer het toegang tot van test API bij *.test.expression.com gebruikend productieauthentiek en vice versa. </p> <p importance="high">Opmerking: De SDK van de Test en het Geavanceerde Hulpmiddel van de Test (ATT) werken slechts met <span class="filepath"> *.test.expressplay.com</span>, terwijl de productieapparaten <span class="filepath"> *.service.expression.com</span> moeten gebruiken. </p> </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> Onvoldoende tokens beschikbaar </td> 
  </tr> 
  <tr> 
   <td> -2020 </td> 
   <td> Type ontbrekende rechten </td> 
  </tr> 
  <tr> 
   <td> -2021 </td> 
   <td> Ongeldig type rechten </td> 
  </tr> 
  <tr> 
   <td> -2022 </td> 
   <td> Eindtijd verhuurperiode ontbreekt </td> 
  </tr> 
  <tr> 
   <td> -2023 </td> 
   <td> Ontbrekende afspeelduur voor verhuur </td> 
  </tr> 
  <tr> 
   <td> -2025 </td> 
   <td> Ongeldige afspeelduur verhuur </td> 
  </tr> 
  <tr> 
   <td> -2027 </td> 
   <td> De coderingssleutel voor inhoud moet 32-hexadecimale cijfers lang zijn </td> 
  </tr> 
  <tr> 
   <td> -2030 </td> 
   <td> ExpressPlay-beheerfout: &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td> Serviceaccount uitgeschakeld </td> 
  </tr> 
  <tr> 
   <td> -2033 </td> 
   <td> Ongeldige cookie </td> 
  </tr> 
  <tr> 
   <td> -2034 </td> 
   <td> Ongeldig uitvoerbesturingselement, waarden buiten opgegeven bereik </td> 
  </tr> 
  <tr> 
   <td> -2035 </td> 
   <td> Geen overeenkomende waarde opgegeven </td> 
  </tr> 
  <tr> 
   <td> -2036 </td> 
   <td> Extensietype moet uit 4 tekens bestaan </td> 
  </tr> 
  <tr> 
   <td> -2037 </td> 
   <td> De payload van de extensie moet Base64-gecodeerd zijn </td> 
  </tr> 
  <tr> 
   <td> -2040 </td> 
   <td><span class="codeph"> </span> OutputControlFlagmust be encode 4 bytes </td> 
  </tr> 
  <tr> 
   <td> -3004 </td> 
   <td> Ongeldige foutindeling opgegeven: &lt;format&gt; </td> 
  </tr> 
  <tr> 
   <td> -4001 </td> 
   <td> Apparaat kon niet worden geverifieerd </td> 
  </tr> 
  <tr> 
   <td> -4018 </td> 
   <td><span class="codeph"> onderliggende </span> ontbreekt </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Failed to get content key from key storage service </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td><span class="codeph"> </span> moet 32 hexadecimale tekens lang zijn </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td><span class="codeph"> De </span> onderliggende items moeten 64 tekens lang na het ^ zijn </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td>Ongeldig <span class="codeph"> kind</span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td>Ongeldige gecodeerde <span class="codeph"> sleutel</span> of kek </td> 
  </tr> 
  <tr> 
   <td> -5001 </td> 
   <td> Fout: onbekend uitvoertype is ongeldig </td> 
  </tr> 
  <tr> 
   <td> -5002 </td> 
   <td> De optie PlayReady is uitgeschakeld voor deze service </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Ongeldige algemene markeringen </td> 
  </tr> 
  <tr> 
   <td> -5004 </td> 
   <td> Apparaat-id moet 32 hexadecimale tekens lang zijn </td> 
  </tr> 
  <tr> 
   <td> -5005 </td> 
   <td> Ongeldige apparaat-id </td> 
  </tr> 
  <tr> 
   <td> -5006 </td> 
   <td> Ontbrekende OPL-waarde </td> 
  </tr> 
  <tr> 
   <td> -5007 </td> 
   <td>Slechts één van <span class="codeph"> kek</span> of <span class="codeph"> contentKey</span> kan worden gespecificeerd </td> 
  </tr> 
 </tbody> 
</table>
