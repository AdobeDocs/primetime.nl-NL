---
description: Als u de DRM-oplossing wilt testen, hebt u een videotoepassing nodig die de specifieke DRM-oplossing kan verwerken waarmee u werkt. Deze speler kan een voorbeeldspeler zijn die beschikbaar wordt gesteld door Adobe of uw eigen videotoepassing op TVSDK.
seo-description: Als u de DRM-oplossing wilt testen, hebt u een videotoepassing nodig die de specifieke DRM-oplossing kan verwerken waarmee u werkt. Deze speler kan een voorbeeldspeler zijn die beschikbaar wordt gesteld door Adobe of uw eigen videotoepassing op TVSDK.
seo-title: Beschermde inhoud afspelen
title: Beschermde inhoud afspelen
uuid: 84f73ee7-43d0-481c-a5e7-14f92169323c
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Beschermde inhoud afspelen {#playback-your-protected-content}

Als u de DRM-oplossing wilt testen, hebt u een videotoepassing nodig die de specifieke DRM-oplossing kan verwerken waarmee u werkt. Deze speler kan een voorbeeldspeler zijn die beschikbaar wordt gesteld door Adobe of uw eigen videotoepassing op TVSDK.

1. Gebruik de URL van de licentieserver van het tokenantwoord dat u hebt gekregen van de ExpressPlay-server om te testen of u de beveiligde inhoud kunt afspelen.

   * **Widevine** - Gebruik de Widevine-reactie direct zoals u hebt ontvangen van uw ExpressPlay-licentietoken-verzoek.
   * **PlayReady** - Haal de URL en het token van de licentieserver op van het JSON-object dat is geretourneerd van uw aanvraag voor het licentietoken.
   * **FairPlay** - Gebruik het FairPlay-antwoord rechtstreeks zoals u hebt ontvangen van uw ExpressPlay-licentietoken-verzoek.

1. Test het afspelen van uw beveiligde inhoud met behulp van uw eigen speler of een bestaande Adobe-voorbeeldspeler.

   Geef de URL voor de beveiligde inhoud op (de locatie van het M3U8- of MPD-manifest, afhankelijk van de DRM-oplossing die u test).

   Afhankelijk van de interface die wordt geleverd door de speler waarmee u test, kan u worden gevraagd om de licentie-URL en het token afzonderlijk te leveren als tekenreeksen in invoervelden, of als een JSON-object dat in een tekstvak wordt geplakt, of misschien als een queryparameter in de URL.

   Hier worden enkele mogelijkheden voor testspelers vermeld:

   * HTML5 Reference Player:

      ```
      https://ptdemos.com/html5/internal/1_2/2.4_GM/samples/reference/reference_player.html
      ```

   * Shaka Player:

      ```
      https://shaka-player-demo.appspot.com
      ```

   * Voorbeeld van TVSDK Player (in ontwikkeling) -

   ```
   https://drmtest2.adobe.com/TVSDK_HTML5/samples/reference/reference_player.html
   ```

   **Het afspelen controleren tijdens het testen van uw FairPlay-instellingen:** FairPlay vereist enkele extra stappen om inhoud af te spelen wanneer u de ExpressPlay-licentieservers gebruikt. Als u uw verbindingen (zoals beschreven in [!DNL curl] Vergunning [) test, moet u uw M3U8 manifest](../../multi-drm-workflows/quick-start/handle-the-licensing.md)(uw verpakte inhoud) als volgt ** uitgeven:

1. Voeg de reactie toe u van uw verzoek van het licentietoken aan de `#EXT-X-KEY:` markering in manifest terugkreeg; en
1. Wijzig het protocol van die URL van de reactie (nu in manifest), van `https://` naar `skd://`.

   Hier volgt een volledig voorbeeld voor het testen van het afspelen met FairPlay, inclusief de licentiesstap:

1. Gebruik de FairPlay-licentietoken-aanvraag om uw licentie-token-URL te verkrijgen. (Gebruik uw eigen Verificator van de Klant van de Productie, en ben zeker om het zelfde CEK te gebruiken en `iv` die werd gebruikt om uw inhoud te verpakken FairPlay.) Voer de volgende opdracht uit om de licentietoken-URL voor de voorbeeldinhoud te verkrijgen:

   ```
   curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
   customerAuthenticator=[YOUR-PRODUCTION-AUTHENTICATOR]&errorFormat=json 
   &contentKey CEK as query parameter contentKey 
   =[YOUR CONTENT KEY]&iv=[YOUR IV]"
   ```

   U krijgt een reactie met de licentietoken-URL die er ongeveer als volgt uitziet:

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g-CR1rn 
   JKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPxN5qomYsnwY 
   SSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw 
   ```

1. Plaats de geretourneerde reactie van het licentietoken-URL in uw M3U8-manifest en *wijzig de regeling van het licentietoken-URL in* `sdk://` from `https://`. Hieronder ziet u een voorbeeld van de tag #EXT-X-KEY in uw manifest van M3U8:

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES, 
   URI="skd://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g- 
   CR1rnJKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPx 
   N5qomYsnwYSSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw", 
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1"
   ```

   >[!NOTE] {Important=&quot;high&quot;}
   >
   >De bovenstaande informatie is alleen van toepassing op het testen van uw FairPlay-instelling. Het is mogelijk niet van toepassing op uw productie-instellingen, afhankelijk van de manier waarop u uw FairPlay-handler configureert. Zie Apple FairPlay [inschakelen in iOS-toepassingen](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md) voor meer informatie.

Als uw video wordt afgespeeld, hebt u uw inhoud in een pakket opgenomen en een licentie gegeven. Als uw video niet wordt afgespeeld, controleer de het oplossen van problemenpagina voor sommige mogelijke oplossingen aan uw problemen.

<!--<a id="example_603D92A1F3924467B5D66EC862B8F59C"></a>-->

Hier ziet u bijvoorbeeld het gedeelte van de gebruikersinterface in de eerste testspeler die hierboven wordt vermeld, waarin u de licentiegegevens opgeeft die zijn verkregen van de ExpressPlay-server:

<!--<a id="fig_zjy_q2c_rw"></a>-->

![](assets/sample-player-drm-settings-web.png)
