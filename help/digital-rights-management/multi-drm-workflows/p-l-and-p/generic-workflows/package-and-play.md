---
description: Met de ExpressPlay's Bento4-packager kunt u inhoud voorbereiden voor alle DRM-oplossingen die worden ondersteund door Primetime Cloud DRM, met ExpressPlay.
seo-description: Met de ExpressPlay's Bento4-packager kunt u inhoud voorbereiden voor alle DRM-oplossingen die worden ondersteund door Primetime Cloud DRM, met ExpressPlay.
seo-title: ExpressPlay Packager / Cloud DRM / TVSDK
title: ExpressPlay Packager / Cloud DRM / TVSDK
uuid: 0d2f5a8d-15c4-42ba-acb8-1dc8d5bc62de
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---


# ExpressPlay Packager / Cloud DRM / TVSDK {#expressplay-packager-cloud-drm-tvsdk}

Met de ExpressPlay&#39;s Bento4-packager kunt u inhoud voorbereiden voor alle DRM-oplossingen die worden ondersteund door Primetime Cloud DRM, met ExpressPlay.

In deze taak wordt beschreven hoe u een hulpprogramma van derden kunt gebruiken om beveiligde inhoud voor te bereiden, in dit geval *ExpressPlay Bento4 Tools*, voor gebruik met verschillende DRM-oplossingen. Raadpleeg de *Bento4-documentatie* op de [ExpressPlay](https://www.expressplay.com/developer/)-website voor meer informatie.
1. Vraag een ExpressPlay-account aan en verkrijg uw ExpressPlay-klantverificatie-gegevens.

   Zie [Primetime DRM Cloud Quick-start.](../../quick-start/quick-overview.md)
1. Als u inhoud voor Toegang Primetime codeert, verkrijg de Toegang SDK van de Adobe van Primetime van Adobe, samen met de vereiste certificaten (Vergunning, Vervoer, en het Verpakken certs).
1. Geef een CEK (Content Encryption Key) en CEKSID (Content Encryption Key Storage ID) op voor gebruik op de DRM-systemen. (U genereert deze willekeurig met OpenSSL of een vergelijkbare methode.)

   De CEK is de werkelijke sleutel waarmee u uw videobestand(en) versleutelt. U slaat het bestand op een veilige manier op uw eigen server op in uw eigen sleutelbeheersysteem, of u kunt gebruikmaken van de [sleutelopslagoplossing](https://www.expressplay.com/developer/key-storage/) van ExpressPlay.

   Een CEKSID is het herkenningsteken voor bepaalde CEK. U geeft (gewoonlijk) de coderingssleutel niet door. Bijvoorbeeld, wanneer het verzoeken van een vergunningsteken, verstrekt u CEKSID.

1. Als u inhoud voor Toegang codeert, gebruik uw CEK om meta-gegevens tot stand te brengen Primetime van de Toegang verbonden aan uw inhoud.

1. Fragmenteer de inhoud om deze voor te bereiden voor het *Bento4 MP4DASH*-gereedschap.

   Voor deze stap kunt u het gereedschap *MP4FRAGMENT* gebruiken. U hoeft de inhoud maar één keer te fragmenteren. Bijvoorbeeld:

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. Met het gereedschap *Bento4 MPDASH* kunt u de gefragmenteerde inhoud &#39;DASH-ify&#39; coderen.

   Gebruik deze opdracht om alle DRM-systemen op te geven die u wilt gebruiken en om eventuele uit de vorige stappen gegenereerde metagegevens voor toegang tot primetime door te geven. Bijvoorbeeld:

   ```
   /mp4dash -f  
   --use-segment-list  
   --use-segment-timeline  
   --encryption-key=<CEKSID>:<CEK>  
   --playready  
   --Widevine  
   --Widevine-header=provider:intertrust#content_id:2a  
   --primetime  
   --primetime-metadata=@AAXS.metadata 
    Fragmented.mp4 -o DASH_OUTPUT
   ```

1. Maak een &quot;storefront server&quot;.

       Deze server moet de volgende bewerkingen uitvoeren:
   
   1. Klantenselectie van inhoud. Deze implementatie moet een eindpunt voor cliënten omvatten om een inhoudstoken voor een specifieke inhoudsidentiteitskaart aan te vragen.
   1. Klantrechten
   1. Aanvragen voor licentietoken (ExpressPlay) van de client ( [ExpressPlay-licentietoken verzoek / reactieverwijzing](../../license-token-req-resp-ref/license-req-resp-overview.md))

1. Maak uw client.

   De client moet een aanroep naar uw winkelserver bevatten. Adobe raadt aan dat de client de storefront aanroept nadat de gebruiker inhoud selecteert en nadat de gebruiker is geverifieerd. Geef vervolgens het token dat door ExpressPlay is geretourneerd, door aan de speler voor licentieaanvragen. Hier vindt u informatie over de implementatie van de DRM-component van uw spelers:

   * TVSDK van browser voor HTML5
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Met het licentietoken in de hand kan de client nu de aanvraag-URL afleiden van het token en de licentieaanvraag indienen bij ExpressPlay. Vervolgens wordt de geselecteerde, beveiligde inhoud voor de gebruiker afgespeeld.
