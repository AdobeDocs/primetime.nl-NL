---
description: 'null'
seo-description: 'null'
seo-title: Modus voor demo van gebruiksmodel configureren
title: Modus voor demo van gebruiksmodel configureren
uuid: f818c7fc-e88f-4fa4-926e-08a1337b28d3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Modus voor demo van gebruiksmodel configureren{#configure-usage-model-demo-mode}

Voordat de server voor Reference Implementation licenties kan uitgeven voor de demo van het gebruiksmodel, moet u de server configureren om op te geven hoe licenties worden gegenereerd voor elk van de vier gebruiksmodellen. Dit betekent u een beleid DRM voor elk gebruiksmodel moet specificeren. De Reference Implementation bevat de volgende voorbeelden van DRM-beleid in de [!DNL Reference Implementation/Server/Reference Implementation Server/resources/] map:

* `dto-policy.pol` - (Downloaden naar eigen keuze)
* `vod-policy.pol` - (huur/video-on-demand)
* `sub-policy.pol` - (Abonnement)
* `ad-policy.pol` - (gefinancierd met ad-hocsteun)

>[!NOTE]
>
>U kunt dit voorbeeldbeleid vervangen door uw eigen DRM-beleid.

1. Stel deze eigenschappen in [!DNL flashaccess-refimpl.properties] om het DRM-beleid op te geven dat u op elk gebruiksmodel wilt toepassen:

   ```
   # DRM Policy file name for Download To Own usage 
   RefImpl.UsageModelDemo.Policy.DTO=dto-policy.pol 
   # DRM Policy file name for Rental usage 
   RefImpl.UsageModelDemo.Policy.VOD=vod-policy.pol 
   # DRM Policy file name for Subscription usage 
   RefImpl.UsageModelDemo.Policy.Subscribe=sub-policy.pol 
   # DRM Policy file name for Ad Supported (free) usage 
   RefImpl.UsageModelDemo.Policy.Free=ad-policy.pol
   ```

1. Kopieer de voorbeeldbeleidsbestanden naar de map die u opgeeft in de `config.resourcesDirectory` eigenschap in [!DNL flashaccess-refimpl.properties].
