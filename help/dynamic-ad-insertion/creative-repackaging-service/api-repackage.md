---
description: U kunt de API voor het opnieuw verpakken van CRS gebruiken om niet-HLS en creatieve producten vooraf te transcoderen, zodat is een versie van HLS beschikbaar wanneer u het moet in werking stellen, eliminerend de 2-4 minieme vertraging verbonden aan just-in-time (JIT) het herverpakken.
seo-description: U kunt de API voor het opnieuw verpakken van CRS gebruiken om niet-HLS en creatieve producten vooraf te transcoderen, zodat is een versie van HLS beschikbaar wanneer u het moet in werking stellen, eliminerend de 2-4 minieme vertraging verbonden aan just-in-time (JIT) het herverpakken.
seo-title: API opnieuw verpakken
title: API opnieuw verpakken
uuid: 03cd2428-510a-4b99-8496-059a48d5abba
translation-type: tm+mt
source-git-commit: 5c026bfc678bafc08f93ad056823e36fd77a8a25

---


# API opnieuw verpakken {#repackaging-api}

U kunt de API voor het opnieuw verpakken van CRS gebruiken om niet-HLS en creatieve producten vooraf te transcoderen, zodat is een versie van HLS beschikbaar wanneer u het moet in werking stellen, eliminerend de 2-4 minieme vertraging verbonden aan just-in-time (JIT) het herverpakken.

## HTTP-aanvraag {#section_F616F5722F0B4AB7939EE2ECBEDDB297}

Verzend een HTTP POST-opdracht naar de opgegeven URL om CRS te laten weten welke en welke creatieve functies u wilt transcoderen en welke opties u wilt gebruiken. De antwoordcode rapporteert succes of mislukking en andere informatie.

Voor deze aanvraag zijn een gebruikersnaam en wachtwoord vereist. U kunt deze aanvragen bij de technische accountmanager van Adobe. Neem contact op met uw Adobe Primetime Enablement-vertegenwoordiger als u informatie over verificatie nodig hebt.

Om een transcoderingsverzoek naar CRS voor te leggen, verzend als volgt een HTTP- bericht:

* **URL -**[https://id3.auditude.com/repackage](https://id3.auditude.com/repackage)

* **Methode -**`POST`

* **Auth -**`Digest`

* **Koptekst -**`Content-Type: text/xml`

* **Body -** XML zoals in het volgende voorbeeld:

   ```xml
   <RepackageList>
       <Repackage>
           <AdSystem>Auditude</AdSystem>
           <AdID>AUD1</AdID>
           <CreativeID>AUD-CR1</CreativeID>
           <CreativeURL>https://cdn.auditude.com/assets/ip/starbucks2.mp4</CreativeURL>
           <Zone>3</Zone>
       </Repackage>
       <Repackage>
           <AdSystem>Auditude</AdSystem>
           <AdID>AUD2</AdID>
           <CreativeID>AUD-CR1</CreativeID>
           <CreativeURL>https://cdn.auditude.com/assets/ip/starbucks2.mp4</CreativeURL>
           <Format>id3 targetdur=5</Format>
           <Zone>3</Zone>
       </Repackage>
   </RepackageList>
   ```

Het `RepackageList` blok in het lichaam kan 1 tot 300 `Repackage` blokken bevatten. Als het aantal `Repackage` blokken in het Body groter is dan 300, mislukt de HTTP-aanvraag met de volgende fout:

```
<codeph>
 HTTP 413 Request Entity Too Large: Validation fail: Too many
     requests. Max limit is 300
</codeph>.
```


De vereiste en facultatieve parameters in een `Repackage` blok zijn als volgt:

* **`AdSystem`** (Vereist) - De bron en server, bijvoorbeeld `Auditude`, `FreeWheel`, `Apad.tv`. Dit is een tekenreekswaarde die overeenkomt met het VAST-element `AdSystem`.

* **`AdId`** (Vereist) - Dit is een id voor de in de aanvraag opgegeven derde partij en server. Het beantwoordt aan de `id` attributen van het `Ad` element in een VAST reactie.

* **`CreativeURL`** (Vereist) - De locatie (URI) van de advertentie die moet worden getranscodeerd. Dit komt overeen met het VAST- `MediaFile` element.

* `CreativeID` (optioneel) - De id voor de creatieve advertentie die moet worden opgenomen als onderdeel van een ad-hocervaring.
* **`Zone`** (Vereist) - zone-id voor uw account (verkrijgbaar bij uw technische accountmanager). Dit is een numerieke waarde die overeenkomt met de `publisher_site_id` instelling van het Auditude-platform.

* **`Format`** (optioneel) - Parameters om te bepalen hoe CRS de advertentie transcodeert:

   * `clientside` - Produceer output compatibel met URL die TVSDK gebruikt om met CDN te communiceren.
   >[!IMPORTANT]
   >
   >U moet deze parameter verstrekken als u wilt dat de herverpakte advertentie compatibel is met de Invoeging van de Zijde van de Cliënt. Als u dit niet doet, zijn de opnieuw verpakte en alleen compatibel met Server Side Ad Insertion.

   * `hls` - Genereer een getranscodeerde en creatieve HLS-compatibele code.
   * `dash` - Genereer een getranscodeerde en creatieve DASH-compatibele code.
   * `id3` - U kunt metagegevenstags met tijdslimiet in de getranscodeerde en creatieve code injecteren.
   * `targetdur` - De duur van het segment (in seconden) voor de getranscodeerde en creatieve gegevens. Standaard is dit `targetdur=4`. Deze waarde moet overeenkomen met de waarde die in het manifest is opgegeven voor `<s>` de tag target duration: `#EXT-X-TARGETDURATION:<s>`.
   >[!NOTE]
   >
   >DASH-compatibele middelen zijn niet compatibel met Adobe Primetime en invoeging.

>[!IMPORTANT]
>
>Voor een vloeiend afspelen moet u deze instellen op de duur van het inhoudssegment. `targetdur`

## HTTP-respons {#section_B30D27E4A6AC4AAD9E758162EFF7D963}

CRS beantwoordt het verzoek met één van de volgende statuscodes:

* **HTTP 202** - Geaccepteerd (met lege hoofdtekst). Dit wijst op succes. CRS uploadt de getranscodeerde en naar de CDN-server.
* **HTTP 400** - Onjuiste aanvraag. De geposte XML is ongeldig.
* **HTTP 500** - Interne serverfout. De server heeft een intern probleem aangetroffen (de server kan bijvoorbeeld geen verbinding maken met een database).

## Pre-transcoderingselementen voor SSAI of CSAI {#section_098888BB74FD4DC1AD0BD507B2A48318}

Met de API voor herverpakken kunt u toekomstige SSAI- of CSAI-gebeurtenissen vooraf transcoderen. Als de activa bestemd zijn om met SSAI in de toekomst te worden gebruikt, zorg ervoor dat alle parameters in de POST vraag uniek zijn. De parameters zijn: AdSystem, AdId, CreativeURL, Zone, Format. Om het even welke verschillen in deze reeks parameters, resulteren in een nieuw transcoderingsverzoek voor SSAI.

Voor elementen die in de toekomst met CSAI worden gebruikt, is de unieke eigenschap voor elementen afhankelijk van Zone en CreativeURL. AdSystem en AdId resulteren niet in verschillende getranscodeerde middelen en deze zijn beschikbaar aan cliënten.
