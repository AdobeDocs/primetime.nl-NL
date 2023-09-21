---
description: Met de ExpressPlay's Bento4-packager kunt u inhoud voorbereiden voor alle DRM-oplossingen die worden ondersteund door Primetime Cloud DRM, met ExpressPlay.
title: ExpressPlay Packager / Cloud DRM / TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ExpressPlay Packager / Cloud DRM / TVSDK {#expressplay-packager-cloud-drm-tvsdk}

Met de ExpressPlay&#39;s Bento4-packager kunt u inhoud voorbereiden voor alle DRM-oplossingen die worden ondersteund door Primetime Cloud DRM, met ExpressPlay.

In deze taak wordt beschreven hoe u een hulpprogramma van derden kunt gebruiken om beveiligde inhoud voor te bereiden. In dit geval *ExpressPlay Bento4-gereedschappen* voor gebruik met diverse DRM-oplossingen. Zie voor meer informatie de *Bento4-gereedschappen* documentatie over de [ExpressPlay](https://www.expressplay.com/developer/) website.
1. Vraag een ExpressPlay-account aan en verkrijg uw ExpressPlay-klantverificatie-gegevens.

   Zie [Primetime DRM Cloud, snel starten.](../../quick-start/quick-overview.md)
1. Als u inhoud voor Toegang Primetime codeert, verkrijg de Toegang SDK van de Adobe Primetime van Adobe, samen met de vereiste certificaten (Vergunning, Vervoer, en het Verpakken certs).
1. Geef een CEK (Content Encryption Key) en CEKSID (Content Encryption Key Storage ID) op voor gebruik op de DRM-systemen. (U genereert deze willekeurig met OpenSSL of een vergelijkbare methode.)

   De CEK is de werkelijke sleutel waarmee u uw videobestand(en) versleutelt. U slaat het bestand op een veilige manier op uw eigen server op in uw eigen sleutelbeheersysteem of u kunt de ExpressPlay-functies gebruiken [belangrijkste opslagoplossing](https://www.expressplay.com/developer/key-storage/).

   Een CEKSID is het herkenningsteken voor bepaalde CEK. U geeft (gewoonlijk) de coderingssleutel niet door. Bijvoorbeeld, wanneer het verzoeken van om een licentietoken, verstrekt u CEKSID.

1. Als u inhoud voor Toegang codeert, gebruik uw CEK om meta-gegevens tot stand te brengen Primetime van de Toegang verbonden aan uw inhoud.

1. De inhoud fragmenteren om deze voor te bereiden op de *Bento4 MP4DASH* gebruiken.

   Voor deze stap kunt u de opdracht *MP4FRAGMENT* gebruiken. U hoeft de inhoud maar één keer te fragmenteren. Bijvoorbeeld:

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. Gebruik de *Bento4 MPDASH* gebruiken om de gefragmenteerde inhoud te &quot;DASH-ify&quot; en te coderen.

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
   1. Aanvragen voor licentietoken (ExpressPlay) van de client ( [ExpressPlay-verzoek voor licentietoken/reactieverwijzing](../../license-token-req-resp-ref/license-req-resp-overview.md))

1. Maak uw client.

   De client moet een aanroep naar uw winkelserver bevatten. De Adobe raadt aan dat de client de storefront aanroept nadat de gebruiker inhoud selecteert en nadat de gebruiker is geverifieerd. Geef vervolgens het token dat door ExpressPlay is geretourneerd, door aan de speler voor licentieaanvragen. Hier vindt u informatie over de implementatie van de DRM-component van uw spelers:

   * TVSDK van browser voor HTML5
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. Met het licentietoken in de hand kan de client nu de aanvraag-URL afleiden van het token en de licentieaanvraag indienen bij ExpressPlay. Vervolgens wordt de geselecteerde, beveiligde inhoud voor de gebruiker afgespeeld.
