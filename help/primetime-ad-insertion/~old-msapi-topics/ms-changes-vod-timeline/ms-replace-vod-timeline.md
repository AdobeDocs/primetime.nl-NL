---
description: De advertentietijdlijn die geschikt is voor het afspelen van VOD-inhoud, is mogelijk niet geschikt voor volgende afspelen. U kunt een VOD-tijdlijn vervangen zonder de inhoud te wijzigen.
title: Wijzigingen in VOD
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Wijzigingen in VOD {#changes-to-vod}

De advertentietijdlijn die geschikt is voor het afspelen van VOD-inhoud, is mogelijk niet geschikt voor volgende afspelen. U kunt een VOD-tijdlijn vervangen zonder de inhoud te wijzigen.

De situaties waarin u een tijdlijn van VOD zou kunnen willen vervangen omvatten:

* Lokale advertenties vervangen, maar nationale advertenties laten staan tijdens een C3-venster.
* Vervang ingebrande advertenties nadat het C3 venster sluit.
* Vervang dynamisch oude C3-advertenties door nieuwere advertenties van langere duur.
* Voeg minder of geen advertenties in.

U kunt de tijdlijn van de advertentie vervangen door een nieuw verzoek tot invoeging in te dienen met het oorspronkelijke M3U8-bestand en een andere waarde van de queryparameter `pttimeline`.