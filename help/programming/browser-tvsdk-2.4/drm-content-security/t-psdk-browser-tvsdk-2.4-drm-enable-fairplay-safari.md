---
description: U kunt FairPlay voor Safari inschakelen wanneer u werkt met Primetime DRM Cloud, aangedreven door ExpressPlay.
title: FairPlay inschakelen voor Safari HLS
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

Als u hier ten volle gebruik wilt maken van de informatie, leert u over Multi-DRM-workflows die beginnen met de subsectie [Referentieserver: Sample ExpressPlay Entitlement Server (SES)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf) in de handleiding voor multi-DRM-workflows. Lees eerst dat de documentatie over het instellen van uw machtiging en sleutelserver veel nuttiger is. De onderstaande informatie is ook nuttig.
U hebt de volgende items nodig:

* Uw *productie* Klantauthenticator van ExpressPlay
* Dezelfde inhoudssleutel en `iv` waarmee uw inhoud is verpakt.
* De locatie van uw openbare-sleutelcertificaat voor FairPlay.

Zo wijzigt u uw FairPlay/Safari-app:

1. Stel de locatie in van uw openbare-sleutelcertificaat voor FairPlay dat is gebruikt in het verzoek van de FairPlay-licentieserver.

   Bijvoorbeeld:

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. Voer een handmatig verzoek voor een FairPlay-licentie *token* uit om een licentie-token-URL op te halen bij ExpressPlay.

       U kunt deze stap op een van de volgende manieren voltooien:
   
   * Gebruik uw eigen ExpressPlay Production-klantverificator.
   * Gebruik dezelfde inhoudssleutel en `iv` in deze aanvraag die is gebruikt om de inhoud te verpakken die u wilt afspelen.

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

1. Voordat uw toepassing beveiligde inhoud kan afspelen, wijzigt u het URL-schema voor de inhoud van `skd://` in `https://`.

   U moet deze wijziging van het URL-schema toevoegen in uw app voordat u de licentieserver aanroept die het afspelen toestaat.

   De protocollen moeten worden veranderd omdat inhoudsidentiteitskaart, die toegang tot de Sleutel van de Inhoud in het Zeer belangrijke Systeem van het Beheer verleent, in M3U8 manifest met het `skd://` protocol verpakt is. Wanneer de speler gereed is om de licentie voor het afspelen van de beveiligde inhoud op te halen, moet deze eerst van protocollen wisselen om te communiceren met de ExpressPlay-licentieserver. In het onderstaande voorbeeld wordt `myServerProcessSPCPath` gewijzigd om het juiste URL-schema voor de aanvraag van de licentieserver te bevatten:

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

