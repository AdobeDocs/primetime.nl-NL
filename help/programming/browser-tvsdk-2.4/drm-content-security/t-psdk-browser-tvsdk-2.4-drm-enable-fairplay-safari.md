---
description: U kunt FairPlay voor Safari inschakelen wanneer u werkt met Primetime DRM Cloud, aangedreven door ExpressPlay.
title: FairPlay inschakelen voor Safari HLS
exl-id: 761c7cb8-3068-44c9-8ceb-6411c509c0a7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# FairPlay inschakelen voor Safari HLS {#enable-fairplay-for-safari-hls}

U kunt FairPlay voor Safari inschakelen wanneer u werkt met Primetime DRM Cloud, aangedreven door ExpressPlay.

Zorg ervoor dat u het volgende hebt:

* Een werkende voorbeeldtoepassing waarmee HLS-video kan worden afgespeeld.

   De voorbeeldapp moet met de via Primetime DRM, met ExpressPlay, afgehandelde licenties beveiligde inhoud kunnen afspelen die door FairPlay is beveiligd.
* Voorbeeld-HLS-inhoud (een M3U8-manifest) verpakt met FairPlay-bescherming.

Als u de informatie hier volledig wilt gebruiken, leert u meer over Multi-DRM-workflows vanaf de subsectie [Referentieserver: Voorbeeld ExpressPlay Entitlement Server (SES)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf) in de handleiding voor multi-DRM-workflows. Lees eerst dat de documentatie over het instellen van uw machtiging en sleutelserver veel nuttiger is. De onderstaande informatie is ook nuttig.
U hebt de volgende items nodig:

* Uw *productie* Customer Authenticator van ExpressPlay
* Dezelfde inhoudssleutel en `iv` waarmee uw inhoud is verpakt.
* De locatie van uw openbare-sleutelcertificaat voor FairPlay.

Zo wijzigt u uw FairPlay/Safari-app:

1. Stel de locatie in van uw openbare-sleutelcertificaat voor FairPlay dat is gebruikt in het verzoek van de FairPlay-licentieserver.

   Bijvoorbeeld:

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. Handmatige FairPlay-licentie uitvoeren *token* verzoek aan ExpressPlay om een licentie-token-URL te verkrijgen.

       U kunt deze stap op een van de volgende manieren voltooien:
   
   * Gebruik uw eigen ExpressPlay Production-klantverificator.
   * Dezelfde inhoudssleutel gebruiken en `iv` in deze aanvraag die is gebruikt om de inhoud te verpakken die u wilt afspelen.

      Voer de volgende opdracht uit vanuit de shell en vervang uw ExpressPlay-klantenauthenticator om de licentietoken-URL voor de voorbeeldinhoud te verkrijgen:

      ```
      curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
           customerAuthenticator=<ExpressPlay customer authenticator identifier>& 
           errorFormat=json& 
           contentKey=<your content key>& 
           iv=<your iv here>"
      ```

      De reactie met de licentie-token-URL ziet er ongeveer als volgt uit:

      ```
      https://fp.service.expressplay.com:80/hms/fp/rights/? 
           ExpressPlayToken=<base64-encoded ExpressPlay token>
      ```

1. Stel een variabele in met de licentietoken-URL van ExpressPlay.

   Bijvoorbeeld:

   ```js
   var myServerProcessSPCPath = 'https://fp.service.expressplay.com:80/hms/fp/rights/? 
        ExpressPlayToken=<base64-encoded ExpressPlay token>';
   ```

1. Voordat uw app beveiligde inhoud kan afspelen, wijzigt u het URL-schema voor de inhoud van `skd://` tot `https://`.

   U moet deze wijziging van het URL-schema toevoegen in uw app voordat u de licentieserver aanroept die het afspelen toestaat.

   De protocollen moeten worden gewijzigd omdat de inhoud-id, die toegang biedt tot de Content Key in het Key Management System, in het M3U8-manifest is verpakt met de `skd://` protocol. Wanneer de speler gereed is om de licentie voor het afspelen van de beveiligde inhoud op te halen, moet deze eerst van protocollen wisselen om te communiceren met de ExpressPlay-licentieserver. In het onderstaande voorbeeld wordt `myServerProcessSPCPath` wordt gewijzigd voor het bevatten van het juiste URL-schema voor de aanvraag van de licentieserver:

   ```js
   extractContentId(initData) {  
       contentId = arrayToString(initData); // contentId is passed up as a URI,  
                                            // from which the host must be extracted:  
       var link = document.createElement('a');  
       link.href = contentId;  
       var index = contentId.indexOf(':');  
       myServerProcessSPCPath = "https:" + contentId.substring(index+1);  
       console.log("severProcessSPCPAth = " + serverProcessSPCPath); return link.hostname;  
   }
   ```
