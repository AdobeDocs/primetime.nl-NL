---
title: Single Sign-On-ondersteuning
description: Single Sign-On-ondersteuning
exl-id: edc3719e-c627-464c-9b10-367a425698c6
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---

# Single Sign-On-ondersteuning

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Overzicht {#overview-sso-support}

In dit document worden de typen Single Sign On beschreven die door Adobe Primetime-verificatie op verschillende platforms worden ondersteund en geactiveerd. Het werkingsgebied van dit document moet licht in wat wordt gesteund en wat niet is, wat is de dekking MVPD voor elke methode SSO en wat van de Programmeurs wordt vereist om van SSO op elk platform te kunnen profiteren.

Nadat een gebruiker met hun geloofsbrieven MVPD het programma opent, produceert de authentificatie van Adobe Primetime een veilig teken dat de zitting van de Authentificatie van MVPD vertegenwoordigt, en bindt dat teken aan het apparaat van de gebruiker gebruikend een identiteitskaart van het Apparaat. Bij Adobe Primetime-verificatie wordt het token/apparaat-id opgeslagen op een server of op het apparaat. Dit staat gebruikers toe om hun geloofsbrieven minder vaak in te gaan terwijl het houden van transacties veilig.

>[!NOTE]
>
>SSO-workflows maken deel uit van het Premium Workflow-pakket. Neem contact op met uw verkoper bij Primetime als u deze functie wilt gebruiken.

## Huidige status van SSO op verschillende platforms {#current-sso-status-platforms}

| Platform/apparaat | SSO-ondersteuning | Type SSO | MVPD-dekking | Notities |
|:-------------------:|:-----------:|:---------------------------------------:|-----------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Web (JavaScript) | Ja | Gedeeld verificatietoken (Adobe SSO) | Alles | Geen SSO voor meerdere browsers Volg de instructies in de Programmer Integration Guide voor JavaScript. Na het volgen van de instructies is SSO standaard ingeschakeld.  Verificatie per aanvrager wordt ingeschakeld en de SSO wordt verbroken |
| iOS | Ja | Platform SSO - tokenuitwisseling | Afhankelijk van Apple-ondersteuning, is de lijst hier | Vanaf iOS 10 introduceerde Apple &amp; Adobe SSO-functionaliteit voor deelnemende programmeurs en MVPD&#39;s. Door de nieuwste Adobe SDK te gebruiken of door de Adobe iOS SDless REST API te gebruiken en de Apple SSO-functionaliteit te implementeren, kunt u profiteren van SSO op iOS-apparaten. Hier vindt u meer informatie over de SDK-implementatie en meer informatie over de implementatie zonder clips. Extra opmerkingen: - Als u Apple SSO niet wilt gebruiken, kunt u nog steeds een beperkte SSO hebben tussen apps van dezelfde leverancier (dezelfde bundle ID) die opslag en een ID (IDFV) kunnen delen. SSO is dus beperkt tot de apps van dezelfde leverancier. |
| Android | Ja | Gedeeld verificatietoken (Adobe SSO) | Alles | Als de gebruiker niet het de toestemmingsverzoek van WRITE_EXTERNAL_STORAGE goedkeurt, zal de bibliotheek een lokale zandbak gebruiken. De implicatie in dit geval is dat er geen SSO tussen verschillende toepassingen zal zijn wanneer het gebruiken van de lokale opslag. |
| tvOS - nieuwe Apple TV | Ja | Platform SSO - tokenuitwisseling | Afhankelijk van Apple-ondersteuning, is de lijst hier | Vanaf tvOS 10 introduceerde Apple &amp; Adobe SSO-functionaliteit voor deelnemende programmeurs en MVPD&#39;s. Door gebruik te maken van de Adobe tvOS SDK of door gebruik te maken van de nieuwste REST API zonder Adobe en de Apple SSO-functionaliteit te implementeren, kunt u profiteren van SSO op tvOS-apparaten. Meer informatie over tvOS SDK: hier en hier voor meer informatie over Clientless-implementatie. |
| Roku | Ja | Gedeeld verificatietoken (Adobe SSO) | Belangrijke volledige lijst voor dekking die binnenkort zal worden verstrekt. | Roku SSO werkt uit de doos met Clientless API voor alle klanten die de richtlijnen van Roku respecteren, geen speciale implementatie wordt vereist. SSO is gebaseerd op de informatie van de apparatenidentificatie die Roku veilig naar Adobe verzendt. |
| Amazon FireTV | Ja | Gedeeld verificatietoken (Adobe SSO) | Belangrijke volledige lijst voor dekking die binnenkort zal worden verstrekt. | FireTV SDK biedt ondersteuning voor Single Sign On op basis van Android-mogelijkheden. De SSO op dit platform is alleen mogelijk tussen apps die momenteel Adobe FireTV SDK gebruiken. Meer informatie over de nieuwe FireTV SDK vindt u hier. FireTV-toepassingen die worden geïmplementeerd boven op de client-API kunnen gebruikmaken van SSO tegen EOY 2018. |
| Xbox 360 | Nee |  |  | Er is geen apparaat-id die we kunnen gebruiken. Er is een toepassings-id, zodat gebruikers deze niet telkens opnieuw hoeven te verifiëren. |
| Xbox One | Nee |  |  | Er is geen apparaat-id die we kunnen gebruiken. Er is een toepassings-id, zodat gebruikers deze niet telkens opnieuw hoeven te verifiëren. |
| Windows 8/10 | Nee |  |  | Er is geen apparaat-id die we kunnen gebruiken. Er is een toepassings-id, zodat gebruikers deze niet telkens opnieuw hoeven te verifiëren. |
| Samsung TV&#39;s | Nee |  |  | Er is geen apparaat-id die we kunnen gebruiken. Er is een toepassings-id, zodat gebruikers deze niet telkens opnieuw hoeven te verifiëren. |

### Opmerkingen over Xbox 360 en Xbox One {#notes-xbox-360}

* **Xbox 360**- Xbox 360 vertrouwt op de Live Service om het token te geven dat de deviceID insluit. De lagen van de Levende Dienst in de appID-waarde voor deviceID, die het werkingsgebied maken slechts aan app. Voor Xbox 360 heeft Microsoft een Java-bibliotheek ter beschikking gesteld om het token te parseren.

* **Xbox One**- Er wordt een JSON-webtoken uitgegeven dat gecodeerd is met de cert/key van de uitgever en ondertekend is door Microsoft. Adobe haalt deviceID uit een parameter genoemd DPI (apparaat Paarsgewijze identiteitskaart), verschillend van de Xbox 360 parameter PDID (identiteitskaart van het Apparaat van de Partner). PDID bestaat ook in Xbox One, maar moet worden vervangen door deze nieuwe parameter &quot;Device Pairwise ID&quot; (DPI).


### SSO uitschakelen {#disable-sso}

In bepaalde situaties zullen sommige apps of sites SSO willen uitschakelen om aan geavanceerde bedrijfssituaties te voldoen.

* **Voor JS en native SDK&#39;s** - Het team van de de authentificatiesteun van Primetime kan SSO voor een vraag ID/MVPD paar onbruikbaar maken. U hoeft niet te werken op sites of in native apps.  Zodra SSO door het team van de de authentificatiesteun van Primetime wordt onbruikbaar gemaakt, zullen de authentificatie die gebruikend het gespecificeerde paar wordt uitgevoerd RequestorId/MVPD niet met plaatsen of apps die verschillende Vraag IDs worden gedeeld. Bovendien zijn bestaande authenticaties met verschillende aanvragers-id&#39;s niet geldig voor de combinatie van aanvrager-id/MVPD waarin SSO is uitgeschakeld. Technisch, wordt SSO het onbruikbaar maken verwezenlijkt door het teken AuthN aan de specifieke combinatie van identiteitskaart van de Aanvrager/MVPD te binden.
* **Voor Clientless-API** - U kunt SSO in de Klantloze authentificatiestroom onbruikbaar maken door een niet-lege appId parameter in de REST vraag te specificeren. U kunt elke tekenreeks als waarde gebruiken, zolang die tekenreeks uniek is voor de aanvrager-id. Voor de API zonder client moet de programmeur/implementator de site of de app wijzigen om deze parameter voor de aanvrager toe te voegen.

>[!IMPORTANT]
>
>BELANGRIJKE OPMERKING VOOR CLIËNTEIT API SSO: Sommige MVPDs vereisen dat elk netwerk (aanvrageridentiteitskaart) zijn eigen authentificatiestroom uitvoert. Voor de op SDK gebaseerde stromen (iOS enz.) wordt dit automatisch door de SDK afgehandeld. Nochtans, voor Clientless APIs moet dit door Programmer worden behandeld. We raden programmeurs ten zeerste aan om SSO-stromen op dit moment niet in te schakelen voor client-API&#39;s en in plaats daarvan een combinatie van apparaat-id en toepassings-id te gebruiken voor apparaat-id. Adobe zal ook werken aan het verbeteren van de Clientless API stromen zodat juiste SSO kan worden gevestigd.

### Afmelden {#logout-sso-support}

Programmeurs moeten zich ervan bewust zijn dat de actie &quot;Afmelden&quot; in de context van Single Sign-On, wanneer uitgevoerd in één app/op één site, alle tokens op het apparaat verwijdert en de gebruiker wordt afgemeld voor apps/sites.

Als aan SSO-voorwaarden wordt voldaan (ongeacht of SSO is ingeschakeld of uitgeschakeld), wordt Afmelden uitgevoerd en worden alle verificatie- en autorisatiegegevens verwijderd.
