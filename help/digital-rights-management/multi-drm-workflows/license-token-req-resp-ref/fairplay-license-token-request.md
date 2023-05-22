---
description: De FairPlay-interface voor licentietoken biedt productie- en testservices.
title: Aanvraag voor FairPlay-licentietoken/reactie
exl-id: 7073a74b-d907-4d45-8550-4305655c33f5
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 4%

---

# Aanvraag en antwoord voor FairPlay-licentietoken {#fairplay-license-token-request-response}

De FairPlay-interface voor licentietoken biedt productie- en testservices. Dit verzoek retourneert een token dat kan worden terugbetaald voor een FairPlay-licentie.

**Methode: GET, POST** (met een www-url-gecodeerd lichaam dat parameters voor beide methodes bevat)

**URL&#39;s:**

* **Productie:** `https://fp-gen.{prod_domain}/hms/fp/token`

* **Testen:** `https://fp-gen.test.expressplay.com/hms/fp/token`

* **Voorbeeldverzoek:**

```<xref href="https: pr-gen.test.expressplay.com="" hms="" pr="" token?customerAuthenticator="201722,1ad8eed133edf43cbcc185f0236828ae&kid=b366360da82e9c6e0b0984002a362cf2&contentKey=b366360da82e9c6e0b0984002a362cf2&rightsType=BuyToOwn&analogVideoOPL=0&compressedDigitalAudioOPL=0&compressedDigitalVideoOPL=0&uncompressedDigitalAudioOPL=0&uncompressedDigitalVideoOPL=0&quot; format=&quot;html&quot; scope=&quot;external&quot;">
  https://fp-gen.test.expressplay.com/hms/fp/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier> 
   &kid=<CEKSID> 
   &contentKey=<CEK> 
   &rightsType=BuyToOwn 
   &analogVideoOPL=0 
   &compressedDigitalAudioOPL=0 
   &compressedDigitalVideoOPL=0 
   &uncompressedDigitalAudioOPL=0 
   &uncompressedDigitalVideoOPL=0
```

* **Samplereactie:**

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

**Query-parameters aanvragen**

**Tabel 3: Parameters tokenquery**

| Query-parameter | Beschrijving | Vereist? |
|--- |--- |--- |
| Customer Authenticator Customer authenticator als query-parameter customerAuthenticator FairPlay | Dit is de API-sleutel van uw klant, één voor uw productie- en testomgeving. U vindt dit op het tabblad ExpressPlay-beheerdashboard. | Ja |
| errorFormat | Of html of json. Als html (het gebrek) een vertegenwoordiging van HTML van om het even welke fouten in het entiteitlichaam van de reactie wordt verstrekt. Als json wordt gespecificeerd, is een gestructureerde reactie in formaat JSON teruggekeerd. Zie [JSON-fouten](https://www.expressplay.com/developer/restapi/#json-errors) voor meer informatie. Het mime-type van de reactie is text/uri-list bij succes, text/html voor de indeling van de HTML-fout of application/json voor de JSON-foutindeling. | Nee |

**Tabel 4: Parameters licentiequery**

| **Query-parameter** | **Beschrijving** | **Vereist?** |
|---|---|---|
| `generalFlags` | Een hexadecimale tekenreeks van 4 bytes die de licentiemarkeringen vertegenwoordigt. &quot;0000&quot; is de enige toegestane waarde. | Nee |
| `kek` | Key Encryption Key (KEK). Toetsen worden gecodeerd met een KEK opgeslagen met behulp van een sleutelomsluitingsalgoritme (AES Key Wrap, RFC3394). Indien `kek` wordt geleverd, een van de `kid` of de `ek` de parameters moeten worden verstrekt; *maar niet beide*. | Nee |
| `kid` | Een hexadecimale tekenreeksrepresentatie van 16 bytes van de coderingssleutel voor inhoud of een tekenreeks `'^somestring'`. De lengte van de tekenreeks, gevolgd door de `'^'` mag niet groter zijn dan 64 tekens. | Nee |
| `ek` | Een hexadecimale tekenreeksrepresentatie van de gecodeerde inhoudssleutel. | Nee |
| `contentKey` | Een hexadecimale tekenreeksrepresentatie van 16 bytes van de coderingssleutel voor inhoud | Ja, tenzij `kek` en `ek` of `kid` worden verstrekt. |
| `iv` | A 16 byte hexadecimale koordvertegenwoordiging van de inhoud encryptie IV | Ja |
| `rentalDuration` | Duur van de huur in seconden (standaardwaarde - 0) | Nee |
| `fpExtension` | Een korte tekstomloop `extensionType` en `extensionPayload`, als een door komma&#39;s gescheiden tekenreeks. Bijvoorbeeld: [...] `&fpExtension=wudo,AAAAAA==&`[...] | Nee, elk nummer kan worden gebruikt |

**Tabel 5: Parameters query-beperking token**

<table id="table_ar3_lsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Query-parameter</b> </th> 
   <th class="entry"> <b>Beschrijving</b> </th> 
   <th class="entry"> <b>Vereist?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> expirationTime </span> </td> 
   <td> Vervaltijd van deze token. Deze waarde MOET een tekenreeks zijn in <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> datum-/tijdnotatie in de zoneaanduiding "Z" ("Zulu-tijd") of een geheel getal voorafgegaan door een plusteken (+). Een voorbeeld van een RFC 3339 datum/tijd is <span class="codeph"> 2006-04-14T12:01:10Z </span>. <p>Als de waarde een tekenreeks is in <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> datum-/tijdnotatie, dan staat deze voor een absolute vervaldatum/tijd voor het token. Als de waarde een geheel getal is dat wordt voorafgegaan door een plusteken (+), wordt deze geïnterpreteerd als een relatief aantal seconden vanaf de uitgifte, dat de token geldig is. </p> Bijvoorbeeld: <span class="codeph"> +60 </span> geeft één minuut aan. De maximum en standaard (als gespecificeerd niet) symbolische levensduur is 30 dagen. </td> 
   <td> Nee </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 6: Zoekparameters correleren**

| **Query-parameter** | **Beschrijving** | **Vereist?** |
|---|---|---|
| `cookie` | Een willekeurige tekenreeks van maximaal 32 tekens die in het token wordt opgenomen en door de tokenterugbetalingsserver wordt geregistreerd. Dit kan worden gebruikt om logboekingangen bij de aflossingsserver en die bij de servers van de dienstverlener te correleren. | Nee |

**Antwoord**

**Tabel 7: HTTP-reacties**

| **HTTP-statuscode** | **Beschrijving** | **Inhoudstype** | **Entiteitslichaam bevat** |
|---|---|---|---|
| `200 OK` | Geen fout. | `text/uri-list` | Aankoop van licentie, URL + token |
| `400 Bad Request` | Ongeldige args | `text/html` of `application/json` | Foutbeschrijving |
| `401 Unauthorized` | Auth failed | `text/html` of `application/json` | Foutbeschrijving |
| `404 Not found` | Ongeldige URL | `text/html` of `application/json` | Foutbeschrijving |
| `50x Server Error` | Serverfout | `text/html` of `application/json` | Foutbeschrijving |

**Tabel 8: Gebeurtenisfoutcodes**

<table id="table_i2c_zsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Code</b> </th> 
   <th class="entry"> <b>Beschrijving</b> </th> 
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
   <td> Verificatietoken ongeldig: &lt;details&gt; <p>Opmerking: Dit kan gebeuren als de authenticator het mis heeft of als de test-API wordt benaderd op <span class="filepath"> *.test.expression.splay.com </span> het gebruik van de authenticator van de productie en omgekeerd. </p> <p importance="high">Opmerking: De SDK van de Test en het Geavanceerde Hulpmiddel van de Test (ATT) werken slechts met <span class="filepath"> *.test.expression.splay.com </span>overwegende dat de productiemiddelen <span class="filepath"> *.service.expressplay.com </span>. </p> </td> 
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
   <td> <span class="codeph"> OutputControlFlag </span> moet 4 bytes coderen </td> 
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
   <td> -4010 </td> 
   <td> Ongeldig token </td> 
  </tr> 
  <tr> 
   <td> -4018 </td> 
   <td> Ontbrekende id </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Failed to get content key from key storage service </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> kind </span> moet 32 hexadecimale tekens lang zijn </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> kind </span> moet 64 tekens lang na het ^ zijn </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> Ongeldig <span class="codeph"> kind </span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td> Ongeldige gecodeerde sleutel of <span class="codeph"> kek </span> </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> Ongeldige algemene markeringen </td> 
  </tr> 
  <tr> 
   <td> -6001 </td> 
   <td> Ongeldig <span class="codeph"> FPExtensions </span> opgegeven parameters </td> 
  </tr> 
  <tr> 
   <td> -6002 </td> 
   <td> Ongeldig type FP-token </td> 
  </tr> 
  <tr> 
   <td> -6003 </td> 
   <td> Ongeldig <span class="codeph"> iv </span> parameter specified </td> 
  </tr> 
  <tr> 
   <td> -6004 </td> 
   <td> Kan CKC voor FP niet genereren </td> 
  </tr> 
  <tr> 
   <td> -6005 </td> 
   <td> Ongeldige sleutelgegevens opgegeven </td> 
  </tr> 
  <tr> 
   <td> -6006 </td> 
   <td> Service niet geautoriseerd voor ondersteuning van FairPlay </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> Ongeldige opgegeven huurduur </td> 
  </tr> 
  <tr> 
   <td> -6008 </td> 
   <td> Binding van apparaat-id wordt niet ondersteund voor FairPlay </td> 
  </tr> 
  <tr> 
   <td> -6009 </td> 
   <td> De optie FairPlay uitgeschakeld </td> 
  </tr> 
 </tbody> 
</table>
