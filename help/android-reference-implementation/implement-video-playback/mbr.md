---
description: De TVSDK kan video's afspelen die meerdere profielen met verschillende bitsnelheden hebben, waarbij van de ene naar de andere gebruiker wordt geschakeld om op basis van de beschikbare bandbreedte meer dan één kwaliteitsniveau te bieden.
title: Meerdere bitsnelheden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---


# Meerdere bitsnelheden {#multiple-bit-rates}

De TVSDK kan video&#39;s afspelen die meerdere profielen met verschillende bitsnelheden hebben, waarbij van de ene naar de andere gebruiker wordt geschakeld om op basis van de beschikbare bandbreedte meer dan één kwaliteitsniveau te bieden.

U kunt aanvankelijke, minimum, en maximumbeetjetarieven evenals het adaptieve beetje-tarief (ABR) schakelaarbeleid voor een veelvoudige stroom van het beetjetarief (MBR) plaatsen. TVSDK schakelt automatisch over naar de bitsnelheid die de beste afspeelervaring biedt binnen de opgegeven configuratie.

De verwijzingsimplementatie vormt de volgende parameters ABR in [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html).

| Parameter | Beschrijving |
|--- |--- |
| Oorspronkelijke bitsnelheid:  getABRInitialBitRate | De gewenste afspeelbitsnelheid (in bits per seconde) voor het eerste segment. Wanneer het afspelen begint, wordt het dichtstbijzijnde profiel (gelijk aan of groter dan de aanvankelijke bitsnelheid) gebruikt voor het eerste segment.  Als een minimale bitsnelheid is gedefinieerd en de aanvankelijke bitsnelheid lager is dan het minimum, selecteert de TVSDK het profiel met de laagste bitsnelheid boven de minimale bitsnelheid. Als de aanvankelijke snelheid boven de maximumsnelheid ligt, kiest de TVSDK de hoogste snelheid onder het maximum. Als de aanvankelijke bitsnelheid nul of ongedefinieerd is, wordt de aanvankelijke bitsnelheid bepaald door het ABR-beleid.  Retourneert een geheel getal dat het byte-per-seconde-profiel vertegenwoordigt. |
| Minimale bitsnelheid:  getABRMinBitRate | Het laagste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief lager dan dit. Retourneert een geheel getal dat het bits-per-seconde-profiel vertegenwoordigt. |
| Maximale bitsnelheid:  getABRMaxBitRate | Het hoogste toegestane beetjetarief waaraan ABR kan schakelen. De omschakeling ABR negeert profielen met een beetjetarief hoger dan dit. Retourneert een geheel getal dat het bits-per-seconde-profiel vertegenwoordigt. |
| ABR-switchbeleid:  getABRPopolicy | De playbackschakelaars geleidelijk aan het hoogste beetje-tarief profiel wanneer mogelijk. U kunt het beleid voor omschakeling plaatsen ABR, die bepaalt hoe snel TVSDK tussen profielen schakelt. De standaardwaarde is Modern. <ul><li>*Conservatief*: Schakelt over naar het profiel met de volgende hogere bitsnelheid wanneer de bandbreedte 50% hoger is dan de huidige bitsnelheid. </li><li>*Gemiddeld*: Schakelt over naar het volgende profiel met een hogere bitsnelheid wanneer de bandbreedte 20% hoger is dan de huidige bitsnelheid.</li><li>*Agressief*: Schakelt onmiddellijk naar het hoogste beetje-tarief profiel wanneer de bandbreedte hoger is dan het huidige beetjetarief</li></ul><br/>Als de aanvankelijke beetjetarief nul of niet gespecificeerd is en een beleid wordt gespecificeerd, begint het playback met het laagste beetje-tarief profiel voor Conservatief, het profiel dichtst bij de mediane beetjetarief van beschikbare profielen voor Matig, en het hoogste beetje-tarief profiel voor Agressive.<br/><br/>Het beleid werkt binnen de beperkingen van de minimum en maximumbeetjetarieven, als zij worden gespecificeerd.  Retourneert de huidige instelling van het opsommingsteken ABRControlParameters: <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>Zie ook  [ABRPopolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html). |

>[!NOTE]
>
>* Het uitvalmechanisme van TVSDK heeft mogelijk voorrang op deze instellingen, omdat TVSDK een continue afspeelervaring voorstaat boven het strikt naleven van de controleparameters.
>* Wanneer de bitsnelheid verandert, verzendt de TVSDK `onProfileChanged`-gebeurtenissen in `PlaybackEventListener`.


## Aangepast ABR-besturingselement inschakelen in de referentie-implementatie {#section_72A6E7263E1441DD8D7E0690285515E6}

De adaptieve bitsnelheid (ABR) wordt standaard ingeschakeld in de TVSDK. U kunt het gebruikersinterface van de Montages van Primetime gebruiken om het standaardgedrag van TVSDK in de verwijzingsimplementatie met voeten te treden door de controle van douaneABR te vormen.

Aangepaste ABR inschakelen via de gebruikersinterface Instellingen:

* Open het dialoogvenster Instellingen Primetime.
* Selecteer **[!UICONTROL ABR controls]**.

   ![](assets/abr-configuration.jpg)

* Tik op het besturingselement [!UICONTROL Enable ON] zodat `OFF` wordt weergegeven.

De `PlaybackManager` plaatst slechts de parameters ABR als [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) waar (ON) terugkeert. Als het vals (UIT) terugkeert, `PlaybackManager` gebruikt de standaardABR controle zodat zal de aanvankelijke, minimum, en maximumbeetjetarieven allen 0 zijn en zal het beleid ABR `ABR_MODERATE` zijn.

## Configureren voor lage bitsnelheden {#section_5451691CBBD24542AD54A474D222CD39}

Bij sommige lage bitsnelheden schakelt de TVSDK standaard over naar de alleen-audio stream en wordt het afspelen bevroren. U kunt de speler zo vormen dat het nooit een situatie ontmoet waar het aan audio-slechts schakelt.

* Implementeer de [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html)-interface:

* Zorg ervoor dat [getABRMinBitRate](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate()) hoger is dan de bitsnelheid alleen-audio (hoger dan 64000).
* Zorg ervoor dat [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled()) is ingeschakeld.