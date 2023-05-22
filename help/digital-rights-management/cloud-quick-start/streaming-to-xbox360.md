---
title: Het XSTS-token instellen in de speler
description: Het XSTS-token instellen in de speler
copied-description: true
exl-id: 1b83baac-e6a6-4e84-8ea5-07bd7e4afd9d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# Streaming naar Xbox360 (optioneel) {#streaming-to-xboc360}

Primetime DRM is beschikbaar op het Xbox360-platform. Maar alleen de Protected Streaming-use-case wordt ondersteund, niet de volledige suite met DRM-beleidsrechten. Niet-streaming DRM-beleidsrechten, zoals apparaatdomeingroepen, worden niet ondersteund. De Xbox 360 negeert niet-ondersteunde rechten wanneer wordt geprobeerd inhoud af te spelen.

De ondersteunde Primetime DRM-beleidsrechten voor de Xbox zijn:
* Digital Output Protection
* Einddatum offlinecache van licentie
* Begindatum van licentie
* Einddatum van licentie
* Tijdsduur afspeelvenster (seconden)

Inhoud hoeft mogelijk niet opnieuw te worden verpakt naar stream naar Xbox360 als deze al is verpakt voor een ander Primetime-platform, zoals iOS, Android of Desktop.

Eén waarschuwing met Xbox360 is dat het altijd naar een sleutelserver moet reiken wanneer een EXT-X-KEY-tag in de M3U8 wordt aangetroffen. In tegenstelling tot iOS, waar een DRM-beleidsinstelling (policy.requireKeyServer) ertoe zal leiden dat de iOS Primetime videospeler de AES-decoderingssleutel van localhost ophaalt, probeert Xbox altijd de decoderingssleutel van een externe sleutelserver op te halen. Er is geen DRM-beleidsrecht om de Xbox-app de coderingssleutel voor AES op te halen van de localhost. Vanwege deze vereiste moeten EXT-X-KEY-items zich bevinden in de M3U8 die wijzen naar het DRM-eindpunt van de Primetime Cloud. Deze URL wordt ingesteld via &lt;key_url> in het OfflinePackager.jar configuratiedossier config_hls.xml.

Als u inhoud één keer wilt verpakken en het stroom aan alle doelstellingen wilt hebben Primetime, evenals iOS apparaten vormen om geen sleutel van verre keyserver terug te winnen, kunt u de inhoud verpakken gebruikend een beleid DRM dat bezitsbeleid.requireKeyServer=false (zoals in policy_ios_localkeyserver.pol) heeft. iOS-apparaten halen de AES-sleutel lokaal op, terwijl Xbox-apparaten deze eigenschap negeren en naar de Primetime Cloud DRM-sleutelserver voor een decoderingssleutel gaan.

>!Note
>
>Alle Xbox 360-aanvragen moeten aangepaste verificatie/>Entitlement gebruiken. Dit komt omdat Xbox Live >op het Xbox 360-platform een Xbox Secure Token Server (XSTS)-token gebruikt voor >verificatiedoeleinden.
>De Primetime Cloud DRM-licentieserver gebruikt de XSTS-token om de integriteit van zowel het Xbox-apparaat als de gebruiker die >de licentieaanvraag maakt, te valideren. Voor de validatie van het XSTS-token is echter een persoonlijke Xbox Live-leverancierstoets van >klant vereist, die niet wordt opgeslagen in Primetime Cloud DRM >niet. Als Primetime Cloud DRM daarom >a licentieaanvraag ontvangt van een Xbox 360-client, stuurt Primetime Cloud DRM >de XSTS-token door naar de back-end >Authentication/Entitlement-server van de Primetime-klant. De Primetime-server van de klant
>parseert en valideert vervolgens het XSTS-token om ervoor te zorgen dat het >ondertekend is met de uitgeversleutel van de toepassing van de klant.
>Als u een XSTS-token wilt doorgeven van de Xbox360-client, stelt u het token >synchroon in als reactie op de gebeurtenis MediaPlayer.RequestKeyAttribute >, zoals hier nader wordt beschreven: **Stel het XSTS-token in de speler in.** Een voorbeeld van een back-end verificatie-/machtigingsserver >is opgenomen in de softwareversie in de directory Custom Authentication >and Entitlement.Validation of XSTS tokens wordt hier >in detail besproken: **Xbox Live XSTS-tokenvalidatie.**


## Het XSTS-token instellen in de speler {#set-the-xsts-token-in-your-player}

In Xbox 360 stelt u het token asynchroon in als reactie op de `MediaPlayer.RequestKeyAttribute` gebeurtenis.

Stel het XSTS-token in.

De voorbeeldtoepassing die bij de software wordt geleverd, laat zien hoe u het XSTS-token in uw speler instelt. Hier volgt het relevante codefragment van de voorbeeldspeler:

```
   MediaPlayer mMediaPlayer;  
 
mMediaPlayer.RequestKeyAttribute += Player_RequestKeyAttribute;  
 
private void Player_RequestKeyAttribute(object sender, RequestKeyAttributeEventArgs args) {  
    string token = "";  
    // XBOX XSTS Token...  
    KeyAttribute keyAttribute = new KeyAttribute(System.Text.Encoding.UTF8.GetBytes(token), null);  
    mMediaPlayer.SetKeyAttribute(args.RequestIdentifier, keyAttribute);  
} 
```

## Xbox Live XSTS-tokenvalidatie {#xbox-live-xsts-token-validation}

Voor XSTS-aanvragen `customerSpecificAuthToken` Het veld bevat het token Base64-codering voor XSTS. Het voorbeeld `XSTSValidator` de code onderzoekt Base64 gedecodeerde teken voor het bestaan van `EncryptedAssertion` element; echter, kunt u andere methodes gebruiken om tussen deze verzoeken en niet-Xbox verzoeken te onderscheiden. U kunt bijvoorbeeld een andere URL gebruiken.

Het beleid dat in het antwoordbericht wordt geretourneerd, overschrijft het oorspronkelijke beleid in de DRM-metagegevens die bij de Xbox key-aanvraag worden geleverd. Slechts wordt een ondergroep van beleidseigenschappen gesteund door de Xbox cliënt, en deze gebieden zijn de enige die het originele beleid zullen met voeten treden.

Er zijn extra opstellingsstappen nodig om symbolische decryptie en bevestiging te steunen. U moet de opdracht [!DNL xsts_partner_cert.pfx] en [!DNL x_secure_token_service.part.xboxlive.com.cer] referenties naar een sleutelarchief met JKS-indelingen, dat u vervolgens aan uw back-end machtigingsserver opgeeft als de eigenschap system `xsts-keystore`. Door gebrek, de partner [!DNL .pfx] heeft de alias `xsts`en het token validation cert heeft de alias `xsts-verify-cert`. U kunt deze ook overschrijven met behulp van systeemeigenschappen. Tot slot is er een systeembezit `xsts-keystore-password` die geen standaardwaarde heeft en die het sleutelarchiefwachtwoord bevat. De systeemeigenschappen die door de `XSTSValidator` de code wordt hieronder samengevat:

| Systeemeigenschap | Standaardwaarde | Opmerking |
|---|---|---|
| xst-keystore | xsts.jks | Het sleutelarchief met JKS-indelingen dat door de validator wordt gebruikt. |
| xsts-keystore-password |  | Wachtwoord voor het sleutelarchief |
| xsts-alias | xsts | Alias die wordt gebruikt om de decryptiesleutel van keystore terug te winnen |
| xsts-verify-cert-alias | xsts-verify-cert | Alias die wordt gebruikt om het validatiecertificaat van keystore terug te winnen |

## JKS maken voor een XSTS-validator{#create-jks-for-an-xsts-validator}

1. Zoek de alias-naam van de persoonlijke cert op die zich in de partner bevindt [!DNL .pfx] bestand.

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. Omzetten [!DNL .pfx] tot [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   waarbij `<alias>` is de alias van de privé cert naam die u in Stap 1 ontdekte.)
1. Importeren [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Put [!DNL xsts.jks] in uw Tomcat-thuismap en definieer `-Dxsts-keystore-password=****` voor Tomcat.

Indien [!DNL xsts_partner_cert.pfx] en [!DNL xsts.jks] gebruikt verschillende wachtwoorden, werkt u de `xsts` wachtwoord in `jks` om ze gelijk te maken.

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
