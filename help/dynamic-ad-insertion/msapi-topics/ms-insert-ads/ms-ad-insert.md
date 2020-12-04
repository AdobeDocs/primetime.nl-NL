---
description: Alle verzoeken om invoeging in een advertentie gebruiken dezelfde URL-structuur en dezelfde basisqueryparameters. De extra vraagparameters laten de duidelijke server toe om met een verscheidenheid van cliënten en situaties te werken.
seo-description: Alle verzoeken om invoeging in een advertentie gebruiken dezelfde URL-structuur en dezelfde basisqueryparameters. De extra vraagparameters laten de duidelijke server toe om met een verscheidenheid van cliënten en situaties te werken.
seo-title: Verzoek om inlassing
title: Verzoek om inlassing
uuid: e42b3228-bff7-4202-86ed-7f631f3016ae
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# Verzoeken om {#requests-for-ad-insertion} toe te voegen

Alle verzoeken om invoeging in een advertentie gebruiken dezelfde URL-structuur en dezelfde basisqueryparameters. De extra vraagparameters laten de duidelijke server toe om met een verscheidenheid van cliënten en situaties te werken.

| Parameter | Beschrijving |
|--- |--- |
| u | De element-id is een MD5-hash van de ad_request_id van de Adobe Primetime en beslissingsmetagegevens. Wordt geleverd door uw Adobe Technical Account Manager. |
| z | De zone-id voor het actief dat aan Auditude moet worden verstrekt. Wordt geleverd door uw Adobe Technical Account Manager. |
| `__sid__` | Een unieke id die de manifestserver zal gebruiken om zitting-id te produceren. |

>[!NOTE]
>
>De parameter `__sid__` wordt omringd door dubbele onderstrepingstekens.

De manifestserver handhaaft zittingen voor individuele cliënten of groepen cliënten om ervoor te zorgen dat de opeenvolgingen van API interactie voor verschillende cliënten afzonderlijk blijven. De `__sid__` die de client in de bootstrap-URL naar de manifestserver verzendt, moet uniek zijn binnen de omgeving. De manifestserver gebruikt het om globaal unieke identiteitskaart te construeren, die het aan de cliënt terugkeert.

De resterende queryparameters hebben betrekking op verschillende clients en situaties.