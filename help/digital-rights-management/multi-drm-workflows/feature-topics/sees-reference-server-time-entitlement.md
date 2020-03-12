---
description: Werk met de SES om te zien hoe u een op tijd gebaseerde machtigingsservice kunt inschakelen met ExpressPlay.
seo-description: Werk met de SES om te zien hoe u een op tijd gebaseerde machtigingsservice kunt inschakelen met ExpressPlay.
seo-title: Referentieservice op tijd gebaseerde machtiging
title: Referentieservice op tijd gebaseerde machtiging
uuid: dd937299-a271-49a9-9b26-eec16f1484df
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Referentieservice: Machtiging op basis van tijd {#reference-service-time-based-entitlement}

Werk met de SES om te zien hoe u een op tijd gebaseerde machtigingsservice kunt inschakelen met ExpressPlay.

De SEES ontvangt een machtigingsverzoek (zie de sectie Public API) van de client. De server SEES kijkt omhoog CEK en IV op basis van `contentID`, voegt toe, `expirationTime`en door:sturen het verzoek aan de server ExpressPlay. Het uiteindelijke ExpressPlay-token is tijdgebonden. Zie het op tijd gebaseerde diagram van de opeenvolging van de Entitlement hieronder. ![](assets/fees-time-based.png)

**Tabel 1: Licentieparameters verzonden door client**

| Query-parameter | Beschrijving | Vereist |
|---|---|---|
| `contentKey` | Een hexadecimale tekenreeksrepresentatie van 16 bytes van de coderingssleutel voor inhoud | Ja |
| `iv` | A 16 byte hexadecimale koordvertegenwoordiging van de inhoud encryptie IV | Ja |
| `rentalDuration` | Duur van de huur in seconden (standaardwaarde = 0) | Nee |

**Tabel 2: De Parameters van de Beperking van het token die door de Server van SEES worden toegevoegd**

<table id="table_E979FAD7A61A4832A46667301939FAEB">  
 <thead> 
  <tr> 
   <th class="entry"> Query-parameter </th> 
   <th class="entry"> Beschrijving </th> 
   <th class="entry"> Vereist? </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> expirationTime</span> </td> 
   <td>Vervaltijd van deze token. Deze waarde moet een tekenreeks zijn in de datum-/tijdnotatie <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" type="external"> RFC 339</a> in de zoneaanduiding 'Z' ('Zulu-tijd') of een geheel getal voorafgegaan door een plusteken (+'). Een voorbeeld van een RFC 3339 datum/tijd is <span class="codeph"> 2006-04-14T12:01:10Z</span>. <p>Als de waarde een tekenreeks in RFC 3339 datum/tijd-indeling is, vertegenwoordigt deze een absolute vervaldatum/tijd voor het token. Als de waarde een geheel getal is dat wordt voorafgegaan door een plusteken (+), wordt deze geïnterpreteerd als een relatief aantal seconden vanaf de afgifte dat de token geldig is. Met <span class="codeph"> +60</span> wordt bijvoorbeeld één minuut opgegeven. De maximale (en standaard, indien niet opgegeven) symbolische levensduur is 30 dagen. Gebruik het gecodeerde formulier "%2B" wanneer u het plusteken (+) opgeeft. </p> </td> 
   <td> Nee </td> 
  </tr> 
 </tbody> 
</table>

