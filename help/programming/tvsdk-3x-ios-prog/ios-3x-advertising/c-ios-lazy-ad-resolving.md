---
description: Oplossen en laden van advertenties kan een onaanvaardbare wachttijd veroorzaken voor een gebruiker die wacht tot het afspelen is gestart. Met de functie Oplossen van laden en neerzetten kunt u deze opstartvertraging verminderen. Advertenties kunnen nu met een opgegeven interval worden opgelost vóór de positie van het ad-einde. Dit wordt bereikt door gebruik te maken van een aanpak met twee spelers.
seo-description: Oplossen en laden van advertenties kan een onaanvaardbare wachttijd veroorzaken voor een gebruiker die wacht tot het afspelen is gestart. Met de functie Oplossen van laden en neerzetten kunt u deze opstartvertraging verminderen. Advertenties kunnen nu met een opgegeven interval worden opgelost vóór de positie van het ad-einde. Dit wordt bereikt door gebruik te maken van een aanpak met twee spelers.
seo-title: Just-in-Time en oplossing
title: Just-in-Time en oplossing
uuid: f7b20439-3604-4d69-bdfe-2e0ad26f495b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Just-in-Time en oplossing {#just-in-time-ad-resolving}

Oplossen en laden van advertenties kan een onaanvaardbare wachttijd veroorzaken voor een gebruiker die wacht tot het afspelen is gestart. Met de functie Oplossen van laden en neerzetten kunt u deze opstartvertraging verminderen. Advertenties kunnen nu met een opgegeven interval worden opgelost vóór de positie van het ad-einde. Dit wordt bereikt door gebruik te maken van een aanpak met twee spelers.

**Eenvoudig proces voor het oplossen en laden van bestanden:**

1. TVSDK downloadt een manifest (playlist) en *lost* alle advertenties op.
1. TVSDK *laadt* alle advertenties en hecht de advertentiesegmenten in de manifesten.
1. TVSDK verplaatst de speler naar de status PREPARED en begint met afspelen van inhoud.

De speler gebruikt de URL&#39;s in het manifest om de advertentie-inhoud (creatieven) te verkrijgen, zorgt ervoor dat de advertentie-inhoud een indeling heeft die TVSDK kan afspelen en dat TVSDK de advertenties op de tijdlijn plaatst. Dit basisproces voor het oplossen en laden van advertenties kan een onaanvaardbare lange wachttijd veroorzaken voor een gebruiker die wacht om zijn inhoud af te spelen, vooral als het manifest meerdere advertentie-URL&#39;s bevat.

**Lazy en oplossen:**

1. TVSDK downloadt de afspeellijst.
1. TVSDK *verhelpt alle pre-roll-advertenties en laadt* deze, verplaatst de speler naar de status PREPARED en begint de inhoud af te spelen.
1. TVSDK *lost* elke advertentie-einden vóór de positie op op basis van de waarde die in `PTAdMetadata::delayAdLoadingTolerance`.

Bijvoorbeeld, door gebrek `delayAdLoadingTolerance` wordt geplaatst aan 5 seconden. Als een AdBreak om 3:00 wordt geplaatst te worden gespeeld, zal het om 2:55:00 worden opgelost. Mogelijk wilt u deze waarde verhogen als u denkt dat de resolutie van uw advertentie langer dan 5 seconden duurt.

>[!IMPORTANT]
>
>**Factoren die in overweging moeten worden genomen met Lazy Ad Resolving:**
>* Lazy Ad Resolving wordt slechts gesteund voor stromen VOD slechts met wijzen SERVER_MAP en signalerende wijze.
>* Lazy Ad Resolving is niet standaard ingeschakeld. U moet `PTAdMetadata::delayAdLoading` = JA plaatsen om het toe te laten.
>* Lazy Ad Resolving is incompatibel met de functie Instant on. Voor meer informatie over Onmiddellijk aan, zie [Onmiddellijk](../../tvsdk-3x-ios-prog/ios-3x-instant-on-ios.md).
>* Beeld-in-beeld-wijze wordt niet gesteund met Lazy en het Oplossen. Schakel de modus Beeld-in-beeld uit als u Oplossen van wazig toevoegen inschakelt.
>* Lazy en resolutie hebben geen invloed op pre-roll advertenties.
>


**Lozy en oplossen inschakelen**

U kunt de functie Oplossen via Lazy en laden in- of uitschakelen via het bestaande mechanisme voor Lazy en oplossen (de functie Oplossen via Lazy en oplossen is standaard uitgeschakeld).

U kunt de functie Lazy Ad Resolving inschakelen door `PTAdMetadata::delayAdLoading`= JA in te stellen bij het instellen van de metagegevens van uw advertentie.

**API&#39;s die relevant zijn voor luie advertentie-resolutie:**

```
Class:    PTAdMetadata 
Properties: 
  
/** 
 * Property to define whether ad break resolution must be delayed until after stream start or not. 
 * When this value is NO, ads are resolved before stream start and spliced into the content when possible allowing  
   for a seamless playback experience. 
 * When this value is YES, ads are displayed in a secondary video player instance and resolved lazily only when  
   needed. 
 * Default value is NO 
 */ 
@property (nonatomic, assign) BOOL delayAdLoading; 
  
/** 
 * Property to define the lookahead for ad break resolution.  Ad breaks will be resolved when they occur between  
   the playhead time and the specified tolerance. 
 * If set to zero, the ad will be resolved immediately before playing the ad.  This may cause a slight delay in the  
   playback of the ads. 
 * Default value is 5.0 or 5 seconds. 
 */ 
  
@property (nonatomic, assign) NSTimeInterval delayAdLoadingTolerance;
```
