---
title: BES-foutcodes
description: BES-foutcodes
copied-description: true
exl-id: 36c83ee9-7e28-442e-8076-691a1bd43a01
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# BES-foutcodes {#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

Als er een fout optreedt tijdens een BES-controle, `DRMErrorEvent` wordt geretourneerd aan de client. U kunt de eigenschappen van deze gebeurtenis parseren om details over de aard van de fout te vinden. Hieronder wordt een subset met mogelijke foutcodes weergegeven.

| Fout | Beschrijving |
|---|---|
| `3304:305` | Generieke autorisatiefout van Primetime Cloud DRM die een verificatie-/autorisatieaanvraag probeert af te handelen. Gewoonlijk is dit niet gekoppeld aan een BES-probleem. Als deze fout voortdurend optreedt, moet u samen met de diagnostische gegevens een probleemticket verzenden naar het Primetime Cloud DRM-team. |
| `3329:0` | Toepassingsspecifieke fout (van de BEES-autorisator). Als er geen subfoutcode is geretourneerd, geeft de fouttekst details van de uitgave weer. Bijvoorbeeld, was er een kwestie die de reactie ontleed, of de server BES was onbereikbaar. |
| `3329:<HTTP error code>` | Een HTTP-antwoord anders dan 200 is uitgegeven door de BES-server. De HTTP-foutcode wordt geretourneerd aan de client in het veld Suberror code. Dit zou op een configuratieprobleem, of een serverstroomonderbreking van BES kunnen wijzen. |
| `3329:<x>` | BES-server HEEFT DE licentieaanvraag UITGESCHAKELD. De subfoutcode en fouttekst worden door de BES-server opgegeven in de JSON-reactie. `error` en `errorText` eigenschappen. Dit soort reactie zou niet als fout, maar eerder een regelmatige ontkenningsreactie van uw server moeten worden beschouwd. |
