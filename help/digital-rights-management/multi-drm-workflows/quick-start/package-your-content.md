---
description: Inhoud verpakken is het proces waarbij video-inhoud wordt voorbereid voor weergave op het web. Het verpakken omvat het omzetten van ruwe video in manifestdossiers, en naar keuze het coderen van de inhoud gebruikend verschillende oplossingen DRM voor verschillende apparaten en browsers.
seo-description: Inhoud verpakken is het proces waarbij video-inhoud wordt voorbereid voor weergave op het web. Het verpakken omvat het omzetten van ruwe video in manifestdossiers, en naar keuze het coderen van de inhoud gebruikend verschillende oplossingen DRM voor verschillende apparaten en browsers.
seo-title: Inhoud verpakken
title: Inhoud verpakken
uuid: b9bc6104-a1ea-4ea0-a0a4-af8a606e5d47
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 0%

---


# Uw inhoud verpakken {#package-your-content}

Inhoud verpakken is het proces waarbij video-inhoud wordt voorbereid voor weergave op het web. Het verpakken omvat het omzetten van ruwe video in manifestdossiers, en naar keuze het coderen van de inhoud gebruikend verschillende oplossingen DRM voor verschillende apparaten en browsers.

Om uw inhoud voor te bereiden, kunt u Adobe Offline Packager of andere hulpmiddelen gebruiken zoals het verpakkingshulpprogramma Bento4 van ExpressPlay. De verpakkers bereiden allebei de video voor playback voor (b.v., die het originele dossier en het zetten van het in manifest), en beschermen de video met uw gekozen oplossing DRM (PlayReady, Widevine, FairPlay, Toegang, enz.):

* [Adobe Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)
* [ExpressPlay-pakketten](https://www.expressplay.com/developer/packaging-tools/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_web.png)

1. Verpak of verkrijg op een andere manier inhoud voor het testen van uw opstelling.

   Een van de cruciale punten die u voor het maken van pakketten moet onthouden, is dat de sleutel-id (Content ID) die u in deze verpakkingsstap gebruikt, dezelfde is als die u in uw volgende licentietoken-aanvraag moet opgeven. De belangrijkste identiteitskaart is het enige punt dat uw CEK identificeert (die in uw eigen zeer belangrijke beheersgegevensbestand kan worden opgeslagen, of gebruikend [de Zeer belangrijke Opslagdienst van ExpressPlay](https://www.expressplay.com/developer/key-storage/) wordt opgeslagen.

   >[!NOTE]
   >
   >Voor degenen die vertrouwd zijn met Adobe Access, is dit een belangrijk verschil in hoe de verschillende oplossingen werken. Bij Access wordt de licentiecode ingesloten in de DRM-metagegevens en doorgegeven aan de beveiligde inhoud. In de multi-DRM systemen die hier worden beschreven, wordt de daadwerkelijke Vergunning niet overgegaan, maar veilig opgeslagen en via Key ID verkregen.

<!--<a id="example_52AF76B730174B79B6088280FCDF126D"></a>-->

Hier volgt een voorbeeld van het verpakken met Adobe Offline Packager for Widevine. Packager gebruikt een configuratiedossier (b.v., [!DNL widevine.xml]), dat iets als dit kijkt:

```
<config> 
<in_path>sample.mp4</in_path> 
<out_type>dash</out_type> 
<out_path>dash2</out_path> 
<drm/> 
<drm_sys>widevine</drm_sys> 
<frag_dur>4</frag_dur> 
<target_dur>6</target_dur> 
<key_file_path>keyfile.bin</key_file_path> 
<widevine_content_id>2a</widevine_content_id> 
<widevine_provider>intertrust</widevine_provider> 
<widevine_key_id>7debe705d938c76bfd886f077b8fa5f7</widevine_key_id> 
</config>
```

* `in_path` - Dit item wijst naar de locatie van de bronvideo op uw lokale verpakkingsapparaat.
* `out_type` - Dit item beschrijft het type van de verpakte uitvoer, in dit geval DASH (voor Widevine Protection on HTML5).
* `out_path` - De locatie op de lokale computer waar u de uitvoer wilt laten gaan.
* `drm_sys` - De DRM-oplossing waarvoor u een verpakking maakt. Dit zal of `widevine`, `fairplay`, of `playready` zijn.

* `frag_dur` en  `target_dur` zijn DASH-specifieke duuritems die betrekking hebben op het afspelen van video.

* `key_file_path` - Dit is de locatie van het licentiebestand op uw verpakkingsapparaat dat als CEK (Content Encryption Key) fungeert. Het is een Base-64 gecodeerde 16-byte hexreeks.
* `widevine_content_id` - Dit is Widevine &quot;Boilerplate&quot;; dat is altijd  `2a`. (Verwar dit niet met `widevine_key_id`.)

* `widevine_provider` - Voor onze doeleinden moet dit altijd worden ingesteld op  `intertrust`.

* `widevine_key_id` - Dit is de id voor de licentie die u in de  `key_file_path` vermelding hebt opgegeven. Met andere woorden, dit identificeert de sleutel u gebruikt om de inhoud te coderen. Deze id is een 16-byte HEX-tekenreeks die u zelf maakt.

Zoals vermeld in [de documentatie van Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf), &quot;als beste praktijken, creeer een configuratiedossier dat de gemeenschappelijke opties bevat die u voor het produceren van de output wilt gebruiken. Maak vervolgens de uitvoer door specifieke opties als opdrachtregelargument op te geven.&quot; In dit geval is ons configuratiebestand redelijk volledig, zodat u de uitvoer als volgt kunt maken:

```
java -jar OfflinePackager.jar -conf_path widevine.xml -out_path test_dash/ 
```

>[!NOTE]
>
>De bevel-lijn parameters nemen belangrijkheid over config- dossierparameters. In dit voorbeeld, is alles vereist in het config- dossier, maar wij hebben de outputweg met voeten getreden die in het config- dossier met `-out_path test_dash/` wordt gespecificeerd.

