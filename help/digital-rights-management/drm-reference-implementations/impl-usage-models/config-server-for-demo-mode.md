---
title: Modus voor demo van gebruiksmodel configureren
description: Modus voor demo van gebruiksmodel configureren
copied-description: true
exl-id: 593acfbd-fd37-4bab-ac8e-5cb62963fac4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Modus voor demo van gebruiksmodel configureren{#configure-usage-model-demo-mode}

Voordat de server voor Reference Implementation licenties kan uitgeven voor de demo van het gebruiksmodel, moet u de server configureren om op te geven hoe licenties worden gegenereerd voor elk van de vier gebruiksmodellen. Dit betekent u een beleid DRM voor elk gebruiksmodel moet specificeren. De implementatie van de Verwijzing omvat het volgende voorbeeldDRM beleid in [!DNL Reference Implementation/Server/Reference Implementation Server/resources/] map:

* `dto-policy.pol` - (Downloaden naar eigen keuze)
* `vod-policy.pol` - (huur/video-on-demand)
* `sub-policy.pol` - (Abonnement)
* `ad-policy.pol` - (gefinancierd met ad-hocsteun)

>[!NOTE]
>
>U kunt dit voorbeeldbeleid vervangen door uw eigen DRM-beleid.

1. Deze eigenschappen instellen in [!DNL flashaccess-refimpl.properties] om het beleid te specificeren DRM dat u van plan bent op elk gebruiksmodel toe te passen:

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

1. Kopieer de voorbeeldbeleidsbestanden naar de map die u opgeeft in het dialoogvenster `config.resourcesDirectory` eigenschap in [!DNL flashaccess-refimpl.properties].
