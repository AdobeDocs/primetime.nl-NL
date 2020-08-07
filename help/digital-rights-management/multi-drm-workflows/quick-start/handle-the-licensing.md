---
description: Licentieverlening is het belangrijkste mechanisme waarbij gebruikers de mogelijkheid wordt geboden of geweigerd om een stuk beveiligde video-inhoud af te spelen. Een wettige (gerechtigde) gebruiker kan een vergunning (een sleutel) worden verleend om een specifiek stuk van de gecodeerde inhoud van zijn inhoudsleverancier te decrypteren en te spelen.
seo-description: Licentieverlening is het belangrijkste mechanisme waarbij gebruikers de mogelijkheid wordt geboden of geweigerd om een stuk beveiligde video-inhoud af te spelen. Een wettige (gerechtigde) gebruiker kan een vergunning (een sleutel) worden verleend om een specifiek stuk van de gecodeerde inhoud van zijn inhoudsleverancier te decrypteren en te spelen.
seo-title: Licentie
title: Licentie
uuid: 9f433d62-5609-4d88-95fd-c1e7c0f6aa75
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# Licentie{#licensing}

Licentieverlening is het belangrijkste mechanisme waarbij gebruikers de mogelijkheid wordt geboden of geweigerd om een stuk beveiligde video-inhoud af te spelen. Een wettige (gerechtigde) gebruiker kan een vergunning (een sleutel) worden verleend om een specifiek stuk van de gecodeerde inhoud van zijn inhoudsleverancier te decrypteren en te spelen.

Voordat uw app of webpagina op het apparaat van een eindgebruiker met DRM beveiligde inhoud kan afspelen, moet deze een token verkrijgen van een machtigings- of storefrontserver die u als klant gebruikt. Adobe biedt hiertoe een voorbeeldreferentieserver: [Referentieserver: Voorbeeld ExpressPlay Entitlement Server (SES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md).

Uw machtiging- of storefront-server vraagt alleen een licentietoken aan bij de relevante ExpressPlay-server nadat u met uw eigen back-end-systemen hebt gecontroleerd of de specifieke gebruiker het recht heeft de gevraagde inhoud te bekijken. De reactie die door de aanvraag voor het licentietoken wordt geretourneerd, is een gebruiksklare URL voor de licentieserver of de reactie bevat de URL in een JSON-structuur, afhankelijk van de DRM-oplossing waarmee u werkt.

>[!NOTE]
>
>De aanvraag voor het licentietoken kan niet van de client zelf worden gedaan:
>1. De rechten moeten in een vertrouwde omgeving worden gecontroleerd; en
>1. De authenticator van de klant moet geheim worden gehouden.


1. Voer de aanvraag voor het licentietoken uit.

   Voor een snel-startscenario, waarin u slechts wilt ervoor zorgen dat de diverse betrokken componenten samenwerken, kunt u iets willen gebruiken als uw verzoek van het licentietoken, (in tegenstelling tot aanvankelijk het krijgen van een app en het testen van vraag van daar). [!DNL curl] Bijvoorbeeld:

   * Widevine:

   ```
   curl "https://wv-gen.test.expressplay.com/hms/wv/token?customerAuthenticator= 
   <Customer Authenticator> 
   &kid 
   <indexterm>
   CEKSID 
     <indexterm>
     as query parameter kid 
    <indexterm>
    Widevine 
    </indexterm> 
    </indexterm> 
    </indexterm>=<CEKSID> 
      &contentKey 
    <indexterm>
    CEK 
    <indexterm>
    as query parameter contentKey 
    <indexterm>
    Widevine 
    </indexterm> 
    </indexterm> 
    </indexterm>=<CEK> 
      &<Any additional licensing attributes desired>" >>WidevineToken 
   ```

   Voorbeeld Widevine-testtoken:

   ```
   https://wv.test.expressplay.com/widevine/RightsManager.asmx?ExpressPlayToken= 
      AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
      RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
      O1PqRkx59Q2q1s2cFNrqfml8Y3RQ 
   ```

   Het Widevine-antwoord is een URL-tekenreeks &quot;gebruiksklaar&quot;.

   * PlayReady:

   ```
   curl "https://pr-gen.test.expressplay.com/hms/pr/token?customerAuthenticator= 
   <Customer Authenticator> 
      &kid 
   <indexterm>
   CEKSID 
   <indexterm>
   as query parameter kid 
   <indexterm>
    PlayReady 
   </indexterm> 
   </indexterm> 
   </indexterm>=<Key ID> 
      &contentKey 
   <indexterm>
    CEK 
    <indexterm>
    as query parameter contentKey 
    <indexterm>
    PlayReady 
   </indexterm> 
   </indexterm> 
   </indexterm>=<CEK> 
      &<Any additional licensing attributes desired>" >>playreadyToken
   ```

   Voorbeeld van PlayReady-testtoken:

   ```
   {"licenseAcquisitionUrl":"https://pr.test.expressplay.com/playready/RightsManager.asmx", 
   "token":"AQAAAxBbWv4AAABgV8_GaWjU80mObLQdfwEdy1lenXmcqvx5VLyqixigtwXLthzjPxq9QDT-TYbudNrMSOpUAy 
   G_2Qt8RdTGJ2_Q_xtRfnj7H6C-yt6By40IhNaSQ0nNYUsY1_MtCrHXIltlVhN2Ekr_RNyTNvCjYs0V5TqzOPY"} 
   ```

   De PlayReady-reactie is een JSON-object met afzonderlijke URL- en token-elementen.

   * FairPlay:

   ```
   curl "https://fp-gen.test.expressplay.com/hms/fp/token?customerAuthenticator= 
    <Customer Authenticator> 
    &kid 
    <indexterm>
      CEKSID 
    <indexterm>
      as query parameter kid 
      <indexterm>
        FairPlay 
      </indexterm> 
    </indexterm> 
    </indexterm>=<Key ID> 
          &contentKey 
    <indexterm>
      CEK 
    <indexterm>
      as query parameter contentKey 
      <indexterm>
        FairPlay 
      </indexterm> 
    </indexterm> 
    </indexterm>=<CEK> 
    &iv=<IV ID> 
    &<Any additional licensing attributes desired>"
   ```

   Voorbeeld van FairPlay-testtoken:

   ```
   https://{expressplay_test_domain_license_url}/?ExpressPlayToken= 
   AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
   RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
   O1PqRkx59Q2q1s2cFNrqfml8Y3RQ
   ```

   Let op: het FairPlay-antwoord is een &quot;gebruiksklare&quot; URL-tekenreeks.
