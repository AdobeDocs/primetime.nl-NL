---
title: Gradatie-API - overzicht
description: Gradatie-API - overzicht
exl-id: c7d6685b-a235-42eb-9c9c-0ffa1747f614
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Gradatie-API - overzicht {#degradation-api-overview}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Algemene informatie {#general_info}

>[!NOTE]
>
>Deze API is niet algemeen beschikbaar. Neem contact op met uw Adobe-vertegenwoordiger voor beschikbaarheidsupdates.

Deze eigenschap verstrekt om het even welke drie partijen in een integratie (Programmers, MVPDs, en Adobe) met de capaciteit om specifieke eindpunten van de Authentificatie en van de Vergunning tijdelijk over te slaan MVPD. Meestal is het de programmeur die een dergelijke actie initieert, maar ongeacht wie een afbraakgebeurtenis activeert, is de actie afhankelijk van eerder overeengekomen regelingen met de betrokken MVPD&#39;s.

Het hoofdgebruik voor deze functie vindt plaats tijdens livesporten of grote evenementen. In dergelijke hoge verkeersscenario&#39;s is het mogelijk voor de lading op een specifiek eindpunt MVPD om te hoog te worden, resulterend in zeer lange reactietijden voor gebruikers. Om een goede gebruikerservaring tijdens zulk een scenario te bewaren, kan de programmeur besluiten om een degradatieregel teweeg te brengen die gebruikers tijdelijk auto-authenticate/auto-autoriseert, of MVPD onbruikbaar te maken door het uit de beschikbare lijst MVPDs te verwijderen.

Een degradatieregel wordt slechts voor een bepaalde periode toegepast. Hoewel de primaire klanten voor deze eigenschap sportkanalen en levende nieuwskanalen zijn, zou om het even welke Programmer toegang tot deze eigenschap kunnen willen hebben, aangezien de diensten MVPDs van tijd tot tijd dalen.

Afbraaknotities:

* Deze eigenschap wordt ontworpen om samen met het gebruik controle API worden gebruikt, die informatie in real time over het aantal voor authentificaties en vergunningen per MVPD, gemiddelde vergunningsvertraging, en andere metriek nodig voor een volledig de dienstoverzicht verstrekt.
* Met deze functie kunt u de Adobe Primetim-verificatieservice niet omzeilen. Als de authentificatie van Primetime neer is is er geen mechanisme binnen de dienst die kan worden gebruikt om gebruikers toe te staan om inhoud te zien. De sites of apps kunnen echter zelf rondom de Primetime-verificatie navigeren.
* Adobe zal momenteel geen directe verslechtering teweegbrengen - het besluit moet altijd bij een specifieke programmeur verblijven die met dergelijke voorwaarden met MVPD&#39;s heeft ingestemd. In de toekomst, kan de authentificatie van Primetime pro-actief in het teweegbrengen van degradatieregels zijn als de overeenkomsten (SLA bescherming) met MVPDs kunnen worden bereikt.

<!--
## Related Information {#related}

- [ESM API](/help/authentication/entitlement-service-monitoring-api.md)
- [Server-side Metrics](/help/authentication/understanding-serverside-metrics.md)
-->
