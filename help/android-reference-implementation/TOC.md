---
cloud: experience-cloud
product: primetime
audience: end-user
user-guide-title: Help bij implementatie van Primetime-naslaggids
user-guide-description: Helpt de TVSDK te begrijpen en de functies te wijzigen om uw persoonlijke speler aan te passen.
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---


# PSDK 1.4 voor Android-naslagimplementatie {#reference-implementation}

+ [Implementatieoverzicht Android-naslaggids](home.md)
+ Primetime referentie-implementatie {#reference}
   + [De Primetime-voorbeeldimplementatie gebruiken](ref-implementation/how-to-use-ref-player.md)
   + [Referentie-implementatiestructuur](ref-implementation/ref-player-structure.md)
   + Hoe te om eigenschapmanagers {#feature-managers} te gebruiken
      + [Hoe te om eigenschapmanagers te gebruiken](ref-implementation/using-feature-managers/how-to-use-feature-managers.md)
      + [Het creëren van eigenschapmanagers door configuratieinformatie tot MediaPlayer over te gaan..](ref-implementation/using-feature-managers/creating-feature-managers.md)
      + [Functies in- of uitschakelen met ManagerFactory](ref-implementation/using-feature-managers/turning-features-on-off.md)
      + [Gebeurtenissen afhandelen](ref-implementation/using-feature-managers/handling-events.md)
   + De ontwikkelomgeving instellen {#setup-dev}
      + [De ontwikkelomgeving instellen](set-up-dev-environment/set-up-dev-environment-overview.md)
      + [Voorwaardelijke software downloaden en configureren](set-up-dev-environment/download-prereqs-android.md)
      + [De implementatie van de Primetime-referentie samenstellen](set-up-dev-environment/install-the-ref-player-project.md)
   + De code {#explore-code} verkennen
      + [PlayerFragment](set-up-dev-environment/exploring-code/player-fragment.md)
      + [Functiemanagers](set-up-dev-environment/exploring-code/about-psdk-feature-managers.md)
      + [ConfigProvider](set-up-dev-environment/exploring-code/config-provider.md)
      + [SettingsActivity](set-up-dev-environment/exploring-code/settings-activity.md)
      + [Catalogusindeling](set-up-dev-environment/exploring-code/catalog-format.md)
      + [JSON-object voor primetime-advertenties](set-up-dev-environment/exploring-code/json-pt-ads.md)
      + [JSON-object voor directe en automatische regeleinden](set-up-dev-environment/exploring-code/json-direct-ad-breaks.md)
      + [JSON-object voor aangepaste advertentiemarkeringen](set-up-dev-environment/exploring-code/json-custom-ad-markers.md)
      + [JSON-object voor machtigingsbron-id](set-up-dev-environment/exploring-code/json-entitlement-resource-id.md)
      + [Voorbeeld JSON-feedindeling](set-up-dev-environment/exploring-code/example-json-feed-format.md)
   + Afspelen van video {#implement-video} implementeren
      + [Essentiële bewerkingen bij het afspelen van video](implement-video-playback/video-playback.md)
      + [Afspelen van video inschakelen](implement-video-playback/enable-video-playback.md)
      + [DRM-inhoudsbeveiliging](implement-video-playback/content-protection.md)
   + [Meerdere bitsnelheden](implement-video-playback/mbr.md)
   + Een speler instellen voor DVR-afspelen met advertenties {#dvr}
      + [DVR zonder invoeging](implement-video-playback/dvr/dvr-without-ad-insertion.md)
      + [DVR met ad-invoeging](implement-video-playback/dvr/dvr-with-ad-insertion.md)
      + [Een aangepast beginpunt voor DVR kiezen](implement-video-playback/dvr/dvr-custom-start-point.md)
      + [Een aangepaste begintijd instellen in de voorbeeldimplementatie](implement-video-playback/dvr/set-custom-start-time-dvr.md)
   + [QoS-afspeelgegevens en apparaatstatistieken weergeven](implement-video-playback/qos-statistics.md)
   + Advertenties {#insert-ads} invoegen
      + [Toevoegen](insert-ads/ad-insertion.md)
      + [Toevoegingstypen](insert-ads/ad-insertion-types.md)
      + [Reclame toevoegen](insert-ads/add-advertising.md)
      + [Gerelateerde API-documentatie](insert-ads/aps-callbacks-ad-insertion.md)
   + Geluid met late binding {#late-binding-audio}
      + [Overzicht](late-binding-audio/late-binding-audio-overview.md)
      + [Laattijdige-binding audio integreren](late-binding-audio/aa-enable.md)
      + [Audiotracks selecteren](late-binding-audio/select-audio-tracks.md)
      + [Gerelateerde API-documentatie](late-binding-audio/aa-api-callbacks.md)
   + Primetime verificatierechten stromen {#primetime-authentications}
      + [Overzicht](paytvpass-entitlement/paytvpass-entitlement-overview.md)
      + [Overzicht van Entitlement Manager](paytvpass-entitlement/entitlement-overvivew.md)
      + [Primetime-verificatie integreren](paytvpass-entitlement/integrate-pass.md)
      + [Adobe Analytics-rapportage configureren](paytvpass-entitlement/pass-analytics-setup.md)
      + [Gerelateerde API-documentatie](paytvpass-entitlement/pass-apis-callbacks.md)
   + Video-analyse {#video-analytics}
      + [Video Analytics](video-analytics/video-analytics-overview.md)
      + [Manager voor videoanalyse maken](video-analytics/create-video-analytics-manager.md)
      + [Video-analyse configureren](video-analytics/configure-video-analytics-manager.md)
      + [Gerelateerde API-documentatie](video-analytics/va-apis-callbacks.md)
   + [Een aangepaste gebruikersinterface maken](build-custom-ui.md)
   + [Problemen oplossen](troubleshooting.md)
