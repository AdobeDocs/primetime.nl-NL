---
description: FER (Full-event replay) is een VOD-middel dat fungeert als een live/DVR-element. Uw toepassing moet daarom stappen ondernemen om ervoor te zorgen dat advertenties correct worden geplaatst.
seo-description: FER (Full-event replay) is een VOD-middel dat fungeert als een live/DVR-element. Uw toepassing moet daarom stappen ondernemen om ervoor te zorgen dat advertenties correct worden geplaatst.
seo-title: Advertenties inschakelen bij volledig afspelen van gebeurtenissen
title: Advertenties inschakelen bij volledig afspelen van gebeurtenissen
uuid: 70e463bd-332c-4f91-ac05-03e79c0939a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Advertenties inschakelen bij volledig afspelen van gebeurtenissen{#enable-ads-in-full-event-replay}

FER (Full-event replay) is een VOD-middel dat fungeert als een live/DVR-element. Uw toepassing moet daarom stappen ondernemen om ervoor te zorgen dat advertenties correct worden geplaatst.

Voor live-inhoud gebruikt TVSDK de metagegevens/aanwijzingen in het manifest om te bepalen waar advertenties moeten worden geplaatst. Soms lijkt het echter wel of levende/lineaire inhoud op VOD-inhoud lijkt. Wanneer de actieve inhoud bijvoorbeeld is voltooid, wordt een `EXT-X-ENDLIST` tag toegevoegd aan het live manifest. Voor HLS betekent de `EXT-X-ENDLIST` tag dat de stream een VOD-stream is. TVSDK kan deze stream niet automatisch onderscheiden van een normale VOD-stream om advertenties correct in te voegen.

Uw toepassing moet TVSDK laten weten of de inhoud live of VOD is door de `AdSignalingMode`inhoud op te geven.

Voor een FER-stream moet de Adobe Primetime- en beslissingsserver niet de lijst met ad-hoconderbrekingen opgeven die op de tijdlijn moeten worden ingevoegd voordat het afspelen wordt gestart. Dit is het gebruikelijke proces voor VOD-inhoud. In plaats daarvan, door een verschillende signalerende wijze te specificeren, leest TVSDK alle richtsnoerpunten van FER manifest en gaat naar de advertentieserver voor elk richtsnoerpunt om een advertentieonderbreking te verzoeken. Dit proces lijkt op live/DVR-inhoud.

Naast elke aanvraag die aan een actiepunt is gekoppeld, doet TVSDK een aanvullende advertentieaanvraag voor pre-roll-advertenties.

1. Van een externe bron, zoals vCMS, verkrijg de signalerende wijze die zou moeten worden gebruikt.
1. Maak de metagegevens die betrekking hebben op reclame.
1. Als het standaardgedrag moet worden beschreven, specificeer `AdSignalingMode` door te gebruiken `AdvertisingMetadata.setSignalingMode`.

   De geldige waarden zijn `DEFAULT, SERVER_MAP`, en `MANIFEST_CUES`.

   U moet de advertentie signalerende wijze plaatsen alvorens `prepareToPlay`te roepen. Nadat TVSDK de bewerkingen voor advertenties heeft opgelost en op de tijdlijn heeft geplaatst, worden wijzigingen in de modus voor advertenties genegeerd. Stel de modus in wanneer u het `AuditudeSettings` object maakt.

1. Doorgaan met afspelen.

<!--<a id="example_3567B4A0D53E4DA99C10C13244454026"></a>-->

