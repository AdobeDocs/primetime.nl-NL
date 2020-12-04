---
description: De gemeenschappelijke problemen tijdens het testen impliceren vaak uw authenticators ExpressPlay, vervoerprotocollen, en vereiste parameters van het de dienstverzoek.
seo-description: De gemeenschappelijke problemen tijdens het testen impliceren vaak uw authenticators ExpressPlay, vervoerprotocollen, en vereiste parameters van het de dienstverzoek.
seo-title: Problemen met uw snelstartoplossing oplossen
title: Problemen met uw snelstartoplossing oplossen
uuid: 42256aa0-2efc-4602-aefc-3bab2dc58ec0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Problemen met uw snelstartverbinding oplossen{#troubleshooting-your-quick-start}

De gemeenschappelijke problemen tijdens het testen impliceren vaak uw authenticators ExpressPlay, vervoerprotocollen, en vereiste parameters van het de dienstverzoek.

Als uw [!DNL curl] verzoeken om ExpressPlay voor symbolengeneratie ontbreken, zal het antwoordlichaam een foutenmelding bevatten die de reden voor mislukking verklaart.

Als het genereren van een token is gelukt maar de inhoud nog steeds niet wordt afgespeeld, controleert u de aflossingslogboeken voor de ExpressPlay-token op fouten zoals &quot;Verlopen token&quot;.

Als het genereren van het token is gelukt en er geen fout is opgetreden en de video nog steeds niet wordt afgespeeld, controleert u of de CEK overeenkomt met de inhoud en of de indeling van de inhoud overeenkomt met de mogelijkheden van het doelapparaat.

Daarnaast:

* Controleer of u de correcte Authenticator van de Klant in uw de dienstverzoeken gebruikt. Het is gemakkelijk om de productieauthenticator per ongeluk te gebruiken wanneer u de testauthenticator wilde gebruiken. Ook, zorg ervoor u *uw* authentificator gebruikt. Tijdens het testen kunt u bijvoorbeeld de opdracht `curl` van iemand anders lenen en vergeten de authenticator voor zijn of haar authenticator in te wisselen.

* Controleer of u het juiste transportprotocol gebruikt in uw aanvragen of in uw manifesten ( `https://` versus `https://`, of in het geval van FairPlay, `skd://` versus `https://` versus `https://`.

* Zorg ervoor dat u alle vereiste vraagparameters voor de oplossing DRM omvat u met werkt. Het is gemakkelijk om tussen PlayReady en Widevine bijvoorbeeld te worden verward, omdat zij allebei met DASH werken, maar de vereiste verzoekparameters en verpakkingsconfiguraties zijn verschillend.
* Bevestig dat je ExpressPlay-account voldoende token-credits heeft en nog niet is gebruikt.
* Bevestig dat het drievoud van DRM-gegevens dat naar de TVSDK wordt verzonden, juist is: ExpressPlay-token, de URL van de licentieserver en het DRM-type.
* Bevestig dat al uw componenten de zelfde veronderstelling maken over welke milieu ExpressPlay in gebruik is aangezien er twee milieu&#39;s, Test en Productie zijn.
* Houd er rekening mee dat verschillende browsers doorgaans slechts één DRM voor DASH-inhoud ondersteunen.
* Vanaf TVSDK 2.4 wordt alleen het DASH-LIVE-pakketprofiel ondersteund. (Ondersteuning voor DASH-OnDemand staat op de routekaart.)
* De ondersteuning voor AndroidTV PlayReady is intermitterend vanwege beperkingen van de fabrikant van apparaten. Om voorbeelden te geven:

   * het Razer Forge-apparaat heeft problemen met PlayReady-inhoud
   * Amazon FireTV kan geen DASH-inhoud gebruiken waarvoor de audiotrack is versleuteld

* Vanaf TVSDK 2.4 ondersteunen alleen AndroidTV-apparaten doorgaans zowel PlayReady- als Windows-DRM&#39;s. Alle andere Android-apparaten ondersteunen doorgaans alleen Widevine.
* Vanaf TVSDK 2.4 vereist de Android-TVSDK momenteel dat het vak PSSH zich in het .mpd-manifest bevindt. Dit is in strijd met de norm DASH, die specificeert dat de doos PSSH overal, zoals in de inhoud zelf, en niet alleen in .mpd kan zijn.

