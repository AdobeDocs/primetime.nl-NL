---
title: BES-foutcodes
description: BES-foutcodes
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# BES-foutcodes {#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

Als er een fout is tijdens een BES-controle, wordt een `DRMErrorEvent` geretourneerd naar de client. U kunt de eigenschappen van deze gebeurtenis parseren om details over de aard van de fout te vinden. Hieronder wordt een subset met mogelijke foutcodes weergegeven.

| Fout | Beschrijving |
|---|---|
| `3304:305` | Generieke autorisatiefout van Primetime Cloud DRM die een verificatie-/autorisatieaanvraag probeert af te handelen. Gewoonlijk is dit niet gekoppeld aan een BES-probleem. Als deze fout voortdurend optreedt, moet u samen met de diagnostische gegevens een probleemticket verzenden naar het Primetime Cloud DRM-team. |
| `3329:0` | Toepassingsspecifieke fout (van de BEES-autorisator). Als er geen subfoutcode is geretourneerd, geeft de fouttekst details van de uitgave weer. Bijvoorbeeld, was er een kwestie die de reactie ontleed, of de server BES was onbereikbaar. |
| `3329:<HTTP error code>` | Een HTTP-antwoord anders dan 200 is uitgegeven door de BES-server. De HTTP-foutcode wordt geretourneerd aan de client in het veld Suberror code. Dit zou op een configuratieprobleem, of een serverstroomonderbreking van BES kunnen wijzen. |
| `3329:<x>` | BES-server HEEFT DE licentieaanvraag UITGESCHAKELD. De code en fouttekst voor de subfout worden door de BES-server opgegeven in de eigenschappen `error` en `errorText` van de JSON-reactie. Dit soort reactie zou niet als fout, maar eerder een regelmatige ontkenningsreactie van uw server moeten worden beschouwd. |