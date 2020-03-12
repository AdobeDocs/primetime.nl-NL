---
description: De Widevine-licentie-tokeninterface biedt productie- en testservices.
seo-description: De Widevine-licentie-tokeninterface biedt productie- en testservices.
seo-title: Token-aanvraag voor Widevine-licentie/reactie
title: Token-aanvraag voor Widevine-licentie/reactie
uuid: a3522422-7075-49a7-bc55-137ef84ee430
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Token-aanvraag voor Widevine-licentie/reactie {#widevine-license-token-request-response}

De Widevine-licentie-tokeninterface biedt productie- en testservices.

Dit HTTP-verzoek retourneert een token dat kan worden ingewisseld voor een Widevine-licentie.

**Methode: GET, POST** (met een www-url-gecodeerde hoofdtekst die parameters voor beide methoden bevat)

**URL&#39;s:**

* **Productie:** `https://wv-gen.{prod_domain}/hms/wv/token`

* **Testen:** ` [https://wv-gen.test.expressplay.com/hms/wv/token](https://wv-gen.test.expressplay.com/hms/wv/token)`

* **Voorbeeldverzoek:**

   ```
   https://wv-gen.service.expressplay.com/hms/wv/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier>
   ```

* **Samplereactie:**

   ```
   https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

<!--<a id="section_1E22012EE4B94BB2974D3B16DE8812D9"></a>-->

**Tabel 13: Parameters tokenquery**

<table id="table_ww1_hcs_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>Query-parameter</b> </th> 
   <th class="entry"> <b>Beschrijving</b> </th> 
   <th class="entry"> <b>Vereist?</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> customerAuthenticator </span> </td> 
   <td> <p>Dit is de API-sleutel van uw klant, één voor uw productie- en testomgeving. U vindt dit op het tabblad ExpressPlay-beheerdashboard. </p> </td> 
   <td> Ja </td> 
  </tr> 
  <tr> 
   <td> <span class="codeph"> errorFormat </span> </td> 
   <td> Of <span class="codeph"> html </span> of <span class="codeph"> json </span>. <p>Als html <span class="codeph"> </span> (de standaardinstelling) een HTML-representatie van fouten bevat in de hoofdtekst van de reactie van de entiteit. Als <span class="codeph"> json </span> wordt gespecificeerd, is een gestructureerde reactie in formaat JSON teruggekeerd. Zie <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON-fouten </a> voor meer informatie. </p> <p>Het mime-type van de reactie is ofwel <span class="codeph"> text/uri-list </span> bij succes, <span class="codeph"> text/html </span> voor <span class="codeph"> HTML- </span> foutindeling, of <span class="codeph"> application/json </span> voor <span class="codeph"> JSON- </span> foutindeling. </p> </td> 
   <td> Nee </td> 
  </tr> 
 </tbody> 
</table>

**Tabel 14: Parameters licentiequery**

| Query-parameter | Beschrijving | Vereist? |
|--- |--- |--- |
| `generalFlags` | Een hexadecimale tekenreeks van 4 bytes die de licentiemarkeringen vertegenwoordigt. &quot;0000&quot; is de enige toegestane waarde | Nee |
| `kek` | Key Encryption Key (KEK). Toetsen worden gecodeerd met een KEK opgeslagen met behulp van een sleutelomsluitingsalgoritme (AES Key Wrap, RFC3394). | Nee |
| `kid` | Een hexadecimale tekenreeksrepresentatie van 16 bytes van de coderingssleutel voor inhoud of een tekenreeks `^somestring'`. De lengte van de tekenreeks gevolgd door de tekenreeks `^` mag niet groter zijn dan 64 tekens. Raadpleeg de onderstaande opmerking voor een voorbeeld. | Ja |
| `ek` | Een hexadecimale tekenreeksrepresentatie van de gecodeerde inhoudssleutel. | Nee |
| `contentKey` | Een hexadecimale tekenreeksrepresentatie van 16 bytes van de coderingssleutel voor inhoud | Ja, tenzij `kek` en `ek` of `kid` |
| `contentId` | Inhoud-id | Nee |
| `securityLevel` | Toegestane waarden zijn 1-5. <ul><li>1 = `SW_SECURE_CRYPTO`</li><li> 2 = `SW_SECURE_DECODE` </li><li> 3 = `HW_SECURE_CRYPTO` </li><li> 4 = `HW_SECURE_DECODE` </li><li> 5 = `HW_SECURE_ALL`</li></ul> | Ja |
| `hdcpOutputControl` | Toegestane waarden zijn 0, 1, 2. <ul><li>0 = `HDCP_NONE` </li><li> 1 = `HDCP_V1` </li><li> 2 = `HDCP_V2`</li></ul> | Ja |
| `licenseDuration` * | Duur van de vergunning in seconden. Indien niet opgegeven, wordt aangegeven dat er geen beperking voor de duur is. Raadpleeg de onderstaande opmerking voor meer informatie. | Nee |
| `wvExtension` | Een kort formulier met extensie Type en extensionPayload, als een door komma&#39;s gescheiden tekenreeks. Zie onderstaande indeling. Voorbeeld: `…&wvExtension=wudo,AAAAAA==&…` | Nee, elk nummer kan worden gebruikt |

Informatie over `licenseDuration`: <ol><li> Het afspelen stopt `licenseDuration` seconden na het starten van het afspelen. </li><li> Als u het afspelen gedurende een onbeperkte tijd wilt stoppen/hervatten, laat u dit weg `licenseDuration` (het afspelen wordt standaard ingesteld op oneindig). Geef anders op hoeveel tijd eindgebruikers van de stream moeten kunnen genieten. </li></ol>

**Tabel 15: Parameters query-beperking token**

| Query-parameter | Beschrijving | Vereist? |
|--- |--- |--- |
| `expirationTime` | Vervaltijd van deze token. Deze waarde MOET een tekenreeks zijn in de datum-/tijdnotatie [RFC 339](https://www.ietf.org/rfc/rfc3339.txt) in de zoneaanduiding &quot;Z&quot; (&quot;Zulu-tijd&quot;) of een geheel getal voorafgegaan door een plusteken. Een voorbeeld van een RFC 3339 datum/tijd is 2006-04-14T12:01:10Z. <br> Als de waarde een tekenreeks in de datum-/tijdnotatie [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) is, vertegenwoordigt deze een absolute vervaldatum/tijd voor het token. Als de waarde een geheel getal is dat wordt voorafgegaan door een plusteken (+), wordt deze geïnterpreteerd als een relatief aantal seconden vanaf de uitgifte, dat de token geldig is. Geeft bijvoorbeeld `+60` één minuut aan. <br> De maximum en standaard (als gespecificeerd niet) symbolische levensduur is 30 dagen. | Nee |

**Tabel 16: Zoekparameters correleren**

| **Query-parameter** | **Beschrijving** | **Vereist?** |
|---|---|---|
| `cookie` | Willekeurige tekenreeks van maximaal 32 tekens bevat het token en is geregistreerd door de tokenterugbetalingsserver. Kan worden gebruikt om logboekingangen bij de aflossingsserver en die bij de servers van de dienstverlener te correleren. | Nee |

<!--<a id="section_6BFBD314C77C40C4B172ABBDD2D8D80E"></a>-->

**Tabel 17: HTTP-respons**

| **HTTP-statuscode** | **Beschrijving** | **Inhoudstype** | **Entiteitslichaam bevat** |
|---|---|---|---|
| `200 OK` | Geen fout. | `text/uri-list` | Aankoop van licentie, URL + token |
| `400 Bad Request` | Ongeldige args | `text/html` of `application/json` | Foutbeschrijving |
| `401 Unauthorized` | Auth failed | `text/html` of `application/json` | Foutbeschrijving |
| `404 Not found` | Ongeldige URL | `text/html` of `application/json` | Foutbeschrijving |
| `50x Server Error` | Serverfout | `text/html` of `application/json` | Foutbeschrijving |

**Tabel 18: Gebeurtenisfoutcodes**

<table id="table_agj_gqx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> Code </th> 
   <th class="entry"> Beschrijving </th> 
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
   <td> Verificatietoken ongeldig: &lt;details&gt; <p>Opmerking:  Dit kan gebeuren als de authenticator het mis heeft of wanneer het toegang tot van test API bij *.test.expression.com gebruikend productieauthentiek en vice versa. </p> <p importance="high">Opmerking:  De test SDK en het Geavanceerde Hulpmiddel van de Test (ATT) werken slechts met <span class="filepath"> *.test.expressplay.com </span>, terwijl de productieapparaten <span class="filepath"> *.service.expressplay.com moeten gebruiken </span> </p>. </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> Onvoldoende tokens beschikbaar </td> 
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
   <td> Ontbrekend <span class="filepath"> kind </span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> Failed to get content key from key storage service </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> child </span> must be 32 hexadecimale characters long </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> onderliggende element </span> moet 64 tekens lang na '^' zijn </td> 
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
   <td> -6005 </td> 
   <td> Ongeldige sleutelgegevens opgegeven </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> Ongeldige opgegeven huurduur </td> 
  </tr> 
  <tr> 
   <td> -7002 </td> 
   <td> Binding van apparaat-id wordt niet ondersteund voor Windows </td> 
  </tr> 
  <tr> 
   <td> -7003 </td> 
   <td> Ontbrekende waarde voor beveiligingsniveau </td> 
  </tr> 
  <tr> 
   <td> -7004 </td> 
   <td> Ongeldige waarde voor beveiligingsniveau </td> 
  </tr> 
  <tr> 
   <td> -7006 </td> 
   <td> Ontbrekende waarde van HDCP-uitvoerbesturingselement </td> 
  </tr> 
  <tr> 
   <td> -7007 </td> 
   <td> Ongeldige licentieduur opgegeven </td> 
  </tr> 
  <tr> 
   <td> -7008 </td> 
   <td> Kan Widevine-licentie niet genereren </td> 
  </tr> 
  <tr> 
   <td> -7009 </td> 
   <td> Ongeldige <span class="codeph"> opgegeven </span> parameters voor WVE-extensie </td> 
  </tr> 
  <tr> 
   <td> -7011 </td> 
   <td> Widevine, optie uitgeschakeld </td> 
  </tr> 
 </tbody> 
</table>