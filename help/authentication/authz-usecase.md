---
title: MVPD Authorization
description: MVPD Authorization
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---


# MVPD Authorization

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Overzicht {#mvpd-authz-overview}

De vergunning (AuthZ) wordt uitgevoerd via backchannel (server-aan-server) mededelingen tussen een Adobe-ontvangen backend server en het eindpunt van AuthZ MVPD.

Voor verzoeken AuthZ, zou het vergunningseindpunt minstens de volgende parameters moeten kunnen verwerken:

* **Uid**. De gebruikers-id die is ontvangen van de verificatiestap.

* **Resource ID**. Een tekenreeks die een bepaalde inhoudsbron identificeert. Deze middelidentiteitskaart wordt gespecificeerd door de Programmer, en MVPD moet de bedrijfsregels betreffende deze middelen versterken (bijvoorbeeld, door te controleren dat de gebruiker aan een bepaald kanaal wordt ingetekend).

Naast het bepalen of de gebruiker een vergunning heeft, moet het antwoord de tijd-aan-levende (TTL) van deze vergunning omvatten, d.w.z. wanneer de vergunning verloopt. Als TTL niet wordt geplaatst, zal het verzoek AuthZ ontbreken.  Daarom **De TTL is een verplichte configuratie die op de authentificatiekant van Adobe Primetime plaatst** om de zaak te behandelen wanneer een MVPD de GVTO niet in hun verzoek opneemt.

## De vergunningsaanvraag {#authz-req}

Een AuthZ-verzoek moet een onderwerp bevatten namens wie het verzoek wordt gedaan, de bron(nen) waartoe het onderwerp toegang probeert te krijgen, de actie die het onderwerp probeert uit te voeren op de bron en de omgeving waarin de bewerking op het punt staat plaats te vinden. In het bijzondere geval van Adobe Primetime-authenticatie komen deze elementen overeen met:

| XACML-element | Komt overeen met |
|---------------|--------------------------------------------------------------------------------------------------------------------------------|
| Onderwerp | Het hoofd dat door de Voor authentiek verklaarde Zitting wordt geïdentificeerd, die door &quot;subject-token&quot;AttributeValue van de bevestiging van SAML wordt van verwijzingen voorzien. |
| Resource | A URI for the Protected Resource. |
| Handeling | WEERGEVEN. |
| Omgeving | Omvat IP adres van de vragende cliënt, zoals die door SP wordt gezien. |



SP op dit punt moet een XACML Authorization DecisionQuery voorbereiden en het verzenden (via de POST van HTTP) naar het (eerder-overeengekomen) Punt van het Besluit van het Beleid (PDP) voor IdP. Hieronder ziet u een voorbeeld van een eenvoudig XACML-verzoek (zie de XACML-kernspecificatie):

```XML
POST https://authz.site.com/XACML_endpoint
<Request  xmlns="urn:oasis:names:tc:xacm:2.0:context:schema:os"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="urn:oasis:names:tc:xacml:2.0:context:schema:os
http://docs.oasis-open.org/xacml/access_control-xacml-2.0-context-schema-os.xsd">
<Subject>
   <Attribute
        AttributeId="urn:oasis:names:tc:xacml:1.0:subject:subject-token"
        DataType="http://www.w3.org/2001/XMLSchema#base64Binary">
      <AttributeValue>{Base64 Data}</AttributeValue>
   </Attribute>
</Subject>
<Resource>
   <Attribute
        AttributeId="urn:oasis:names:tc:xacml:1.0:resource:resource-id"
        DataType="http://www.w3.org/2001/XMLSchema#anyURI">
<AttributeValue>urn:tve:tms:1234</AttributeValue>
   </Attribute>
</Resource>
<Action>
   <Attribute
        AttributeId="urn:oasis:names:tc:xacml:1.0:action:action-id"
        DataType="http://www.w3.org/2001/XMLSchema#string">
       <AttributeValue>VIEW</AttributeValue>
   </Attribute>
</Action>
<Environment>
   <Attribute
       AttributeId="urn:oasis:names:tc:xacml:1.0:subject:authn-locality:ip-address"
       DataType="http://www.w3.org/2001/XMLSchema#string">
      <AttributeValue>1.2.3.4</AttributeValue>
   </Attribute>
</Environment>
</Request>
```


Na het ontvangen van het verzoek AuthZ, evalueert PDP van MVPD het verzoek en bepaalt of het onderwerp zou moeten worden toegestaan om de gevraagde actie op het middel uit te voeren. Het MVPD keert dan een antwoord met een Besluit, een code van de Status, en een bericht terug, zoals die in de Reactie van de Toestemming hieronder worden beschreven.

## De machtigingsreactie {#authz-response}

De reactie op het verzoek AuthZ komt nadat MVPD het verzoek evalueert en past de gevraagde bedrijfsregels toe om te bepalen als het onderwerp de gevraagde actie op het middel mag uitvoeren. De teruggekeerde Reactie op de authentificatie van Adobe Primetime wordt opnieuw uitgedrukt na de XACML kernspecificatie met een Besluit, een code van de Status, een bericht, en de Verplichtingen die SP als het Punt van de Handhaving van het Beleid (PEP) heeft. Hier volgt een voorbeeldreactie:

```XML
<Response xmlns="urn:oasis:names:tc:xacml:2.0:context:schema:os">
  <Result>
  <Decision>Permit</Decision>
  <Status>
     <StatusCode Value="urn:oasis:names:tc:xacml:1.0:status:ok"/>
     <StatusMessage>ok</StatusMessage>
  </Status>
  <xacml:Obligations     
          xmlns:xacml="urn:oasis:names:tc:xacml:2.0:policy:schema:os">
     <xacml:Obligation    
              ObligationId="urn:cablelabs:olca:1.0:obligations:log"
              FulfillOn="Permit" />
  </xacml:Obligations>
 </Result>
</Response>
```

Hieronder volgt een lijst met DENY-verplichtingen die door Adobe Primetime-verificatie worden ondersteund en waarmee programmeurs kunnen voldoen:

* **urn:tve:xacml:2.0:obligations:restrict-pc** - De abonnee heeft geen ouderlijke controle uitgevoerd en de SP moet passende maatregelen nemen om de toegang tot deze inhoud te beperken.

* **urn:tve:xacml:2.0:obligations:upgrade** - De abonnee heeft geen geschikt soort abonnement.  U moet een upgrade uitvoeren op uw abonnement om toegang te krijgen tot inhoud.

Adobe Primetime-verificatie ondersteunt het volgende **VERGUNNING** Verplichtingen en mogelijkheden voor programmeurs om aan deze verplichtingen te voldoen:

* **urn:cablelabs:olca:1,0:obligations:log** - Adobe Pass registreert de transactie en kan deze beschikbaar stellen via het overeengekomen rapportagemechanisme.

* **urn:cablelabs:olca:1,0:obligations:herschrijven** - Adobe Primetime-verificatie vernieuwt de autorisatie in n seconden opnieuw (opgegeven als een argument voor de verplichting via een XACML AttributeAssignment - zie XACML core spec, Section 5.46).

<!--
>![RelatedInformation]
>* [Preflight Authorization](/help/authentication/preflight-authz.md)
>* [Authentication](/help/authentication/authn-usecase.md)
-->