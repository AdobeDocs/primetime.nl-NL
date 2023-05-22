---
description: Alle verzoeken om invoeging in een advertentie gebruiken dezelfde URL-structuur en dezelfde basisqueryparameters. De extra vraagparameters laten de duidelijke server toe om met een verscheidenheid van cliënten en situaties te werken.
title: Verzoek om inlassing
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Verzoek om inlassing {#requests-for-ad-insertion}

Alle verzoeken om invoeging in een advertentie gebruiken dezelfde URL-structuur en dezelfde basisqueryparameters. De extra vraagparameters laten de duidelijke server toe om met een verscheidenheid van cliënten en situaties te werken.

| Parameter | Beschrijving |
|--- |--- |
| u | De element-id is een MD5-hash van de ad_request_id van de Adobe Primetime en beslissingsmetagegevens. Wordt geleverd door uw Adobe Technical Account Manager. |
| z | De zone-id voor het actief dat aan Auditude moet worden verstrekt. Wordt geleverd door uw Adobe Technical Account Manager. |
| `__sid__` | Een unieke id die de manifestserver zal gebruiken om zitting-id te produceren. |

>[!NOTE]
>
>De `__sid__` parameter wordt omgeven door dubbele onderstrepingstekens.

De manifestserver handhaaft zittingen voor individuele cliënten of groepen cliënten om ervoor te zorgen dat de opeenvolgingen van API interactie voor verschillende cliënten afzonderlijk blijven. De `__sid__` dat de cliënt in bootstrap URL naar de manifestserver verzendt uniek binnen zijn milieu zou moeten zijn. De manifestserver gebruikt het om globaal unieke identiteitskaart te construeren, die het aan de cliënt terugkeert.

De resterende queryparameters hebben betrekking op verschillende clients en situaties.