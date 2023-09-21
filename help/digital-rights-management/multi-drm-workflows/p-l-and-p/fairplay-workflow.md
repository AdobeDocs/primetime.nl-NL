---
description: De DRM-workflows omvatten het verpakken van uw inhoud, het verstrekken van licenties voor de inhoud en het afspelen van de beveiligde inhoud vanuit uw eigen videotoepassing. De workflow is over het algemeen vergelijkbaar voor elke DRM-oplossing, maar met enkele verschillen zijn de details.
title: Multi-DRM-workflow voor FairPlay
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1470'
ht-degree: 0%

---

# Multi-DRM-workflow voor FairPlay {#multi-drm-workflow-for-fairplay}

De DRM-workflows omvatten het verpakken van uw inhoud, het verstrekken van licenties voor de inhoud en het afspelen van de beveiligde inhoud vanuit uw eigen videotoepassing. De workflow is over het algemeen vergelijkbaar voor elke DRM-oplossing, maar met enkele verschillen zijn de details.

Deze workflow met Multi-DRM begeleidt u door het instellen, verpakken, licentiëren en afspelen van HLS-inhoud die is beveiligd met Apple FairPlay. Deze workflow bevat ook optionele instructies voor het implementeren van offline afspelen en het roteren van licenties.

## ExpressPlay-service inschakelen voor FairPlay {#enable-expressplay-service-for-fairplay}

De FairPlay DRM-oplossing van Apple vereist enige configuratie wanneer u deze gebruikt met de ExpressPlay DRM-services. Dit betekent dat u gebruikersgegevens van Apple opgeeft en deze uploadt naar ExpressPlay.

Voer de volgende stappen uit om de ExpressPlay-service voor de bescherming van FairPlay-inhoud in te schakelen.

1. Verkrijg gegevens van Apple.

   Deze geloofsbrieven worden verstrekt uniek aan elke dienstverlener. U moet deze aanvragen door het volgende formulier in te vullen: [https://developer.apple.com/contact/fps/](https://developer.apple.com/contact/fps/).

   >[!NOTE]
   >
   >Selecteren **[!UICONTROL Content Provider]** voor primaire rol.

   Zodra je aanvraag is goedgekeurd, stuurt Apple je een *Implementatiepakket voor FairPlay-streaming*.
1. Genereer een certificaataanvraag.

   U kunt [!DNL openssl] om uw openbare/privé zeer belangrijke paar, en uw certificaat ondertekende verzoek (CSR) te produceren.

   1. Genereer uw sleutelpaar.

      ```
      openssl genrsa -aes256 -out privatekey.pem 1024 
      ```

   1. Genereer uw CSR.

      ```
      openssl req -new -sha1 -key privatekey.pem -out certreq.csr  
        -subj "/CN=SubjectName /OU=OrganizationalUnit /O=Organization /C=US"
      ```

      >[!NOTE]
      >
      >De instructies voor deze stap bevinden zich in uw *Implementatiepakket voor FairPlay-streaming*, maar worden hier voor uw gemak opgenomen. Als u problemen hebt met dit onderdeel van het proces, raadpleegt u de instructies in *FairPlayCertificateCreation.pdf* (in uw implementatiepakket).

1. Upload uw CSR via de Apple Developer Portal.
   1. De Agent van het Team voor uw ontwikkelingsteam moet login [!DNL developer.apple.com/account].
   1. Klikken op **[!UICONTROL Certificates, Identifiers & Profiles]** en selecteert u vervolgens de **[!UICONTROL iOS, tvOS, watchOS]** vervolgkeuzelijst linksboven op de pagina en klik vervolgens op **[!UICONTROL Certificates->Production]** links op de pagina.
   1. Klik op de knop **[!UICONTROL +]** rechtsboven op de pagina om een nieuw certificaat aan te vragen. Selecteer de **[!UICONTROL FairPlay Streaming Certificate]** optie onder **[!UICONTROL Production]**.

      De *IOS-certificaat toevoegen* wordt geopend.
   1. In de *IOS-certificaat toevoegen*, uploadt u het CSR-bestand dat u in Stap 2.b hebt gegenereerd en klikt u op **[!UICONTROL Generate]**.

      Uw Sleutel van het Geheime van de Toepassing (ASK) wordt getoond in de zelfde dialoog.
   1. Noteer uw ASK en bewaar deze op een veilige plaats.
   1. Sleutel in uw ASK om certificaatgeneratie te voltooien en klik **[!UICONTROL Continue]**.
   1. Nadat u hebt geverifieerd dat u de ASK hebt opgeslagen, klikt u op **[!UICONTROL Generate]** om door te gaan.

      >[!NOTE]
      >
      >Het is belangrijk dat u een kopie van uw ASK opslaat en deze veilig opslaat. *Als uw ASK gecompromitteerd is, kunt u uw inhoud niet meer beschermen met FairPlay Streaming.* Slechts één (1) ASK wordt toegewezen aan uw team. De waarde wordt niet opnieuw opgegeven en u kunt deze later niet ophalen.

   1. Download uw FPS-certificaat.

      Sla een reservekopie van uw persoonlijke sleutel (uit stap 2.a.) en uw openbare sleutel (het FPS-certificaat dat u in deze stap hebt gedownload) op een veilige plaats op.
1. Stel uw ExpressPlay-account in met uw FairPlay-referenties.
   1. De certificaatnaam die u in Stap 3.h hebt gedownload, is [!DNL fairplay.cer].
   1. Open de [!DNL fairplay.cer] bestand met het Apple Keychain Access-hulpprogramma.
   1. Filter uw vele certificaten door &quot; `fairplay`&quot; in het zoekveld rechtsboven.
   1. Identificeer het FairPlay-certificaat van uw bedrijf.

      Uw bedrijfsnaam moet zijn gekoppeld aan het certificaat dat door Apple is uitgegeven.
   1. Vouw het certificaat uit door de pijl uitvouwen te selecteren en met de rechtermuisknop op de persoonlijke sleutel te klikken.
   1. Selecteren **[!UICONTROL Export "Your Company Name"]** en sla de [!DNL .p12] bestand.

      U wordt gevraagd een wachtwoord toe te wijzen om dit bestand te beveiligen. Noteer dit wachtwoord omdat u dit samen met het aanmeldingspakket moet verzenden.
   1. Aanmelden bij uw account op [www.expressplay.com](https://www.expressplay.com).
   1. Klikken **[!UICONTROL DRM SERVICES]** in de linkerbovenhoek selecteert u vervolgens de knop **[!UICONTROL FairPlay]** tab.
   1. Upload uw FairPlay-referenties naar uw ExpressPlay-account.

      1. Maak een tekstbestand dat de waarde van de ASK bevat (dit moet 32 tekens zijn, bijvoorbeeld: `1234567890abcdef1234567890abcdef`) en selecteer dit bestand om te uploaden.
      1. Selecteer het PKCS12-bestand in stap 4.f voor uploaden.
      1. Voer het PKCS12-bestandswachtwoord uit stap 4.f in.
      1. Klik op de knop Uploaden.

Nu kunt u iOS-toepassingen of HTML5-pagina&#39;s maken met de beveiliging van FairPlay-inhoud, samen met uw [!DNL fairplay.cer] certificaat met de ExpressPlay-service voor FairPlay.

<!--<a id="fig_sjr_2pn_sv"></a>-->

![](assets/multi_drm_expressplay_drm_services_web.png)

### Inhoud verpakken voor FairPlay {#package-your-content-for-fairplay}

Als u inhoud wilt verpakken, kunt u Adobe Offline Packager of andere gereedschappen gebruiken, zoals de Bento4-pakketsoftware van ExpressPlay.

Pakketten bereiden de video voor op afspelen (bijvoorbeeld door het oorspronkelijke bestand te splitsen en in een manifest te plaatsen) en beschermen de video met de door u gekozen DRM-oplossing (in dit geval FairPlay):

* [Offline Adobe Packager for FairPlay DRM](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=21)
* [ExpressPlay-pakketten - Bento4 voor HLS](https://www.bento4.com/developers/hls/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_hls_web.png)

1. Verpak uw inhoud.

   Hier volgt een voorbeeld van het verpakken met Adobe Offline Packager. Packager gebruikt een configuratiebestand (bijvoorbeeld [!DNL fairplay.xml]), die er ongeveer als volgt uitziet:

   ```
   <config>
   <in_path>mp4_file_path</in_path>
   <out_type>hls</out_type>
   <out_path>out_file_path</out_path>
   <drm/>
   <drm_sys>FAIRPLAY</drm_sys>
   <frag_dur>4</frag_dur>
   <target_dur>6</target_dur>
   <key_file_path>creds/fairplay.bin</key_file_path>
   <iv_file_path>creds/iv.bin</iv_file_path>
   <key_url>user_provided_value</key_url>
   <content_id>_default_</content_id>
   </config>
   ```

   * `in_path` - Dit item wijst naar de locatie van de bronvideo op uw lokale verpakkingsapparaat.
   * `out_type` - Deze vermelding beschrijft het type van de verpakte uitvoer, in dit geval HLS voor FairPlay.
   * `out_path` - De locatie op de lokale computer waar u de uitvoer wilt laten gaan.
   * `drm_sys` - De DRM-oplossing waarvoor u een verpakking maakt. Dit is `FAIRPLAY` in dit geval.
   * `frag_dur` - De fragmentduur in seconden.
   * `target_dur` - De doelduur voor HLS-uitvoer.
   * `key_file_path` - Dit is de locatie van het licentiebestand op uw verpakkingsapparaat dat als CEK (Content Encryption Key) fungeert. Het is een Base-64 gecodeerde 16-byte hexreeks.
   * `iv_file_path` - Dit is de locatie van het IV-bestand op uw verpakkingsapparaat.
   * `key_url` - De URI-parameter van de `EXT-X-KEY` tag van de [!DNL .m3u8] bestand.
   * `content_id` - Standaardwaarde.

   Zoals vermeld in het [Packager-documentatie](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=7), &quot;Als beste praktijken, creeer een configuratiedossier dat de gemeenschappelijke opties bevat die u voor het produceren van de output wilt gebruiken. Maak vervolgens de uitvoer door specifieke opties als opdrachtregelargument op te geven.&quot;

   ```
   java -jar OfflinePackager.jar -in_path sample.mp4 -out_type hls 
   -out_path out_file_path -drm -drm_sys FAIRPLAY -key_file_path "creds/fairplay.bin" 
   -key_url "user_provided_value"
   ```

   Het gegenereerde M3U8-bestand heeft een `EXT-X-KEY` kenmerk dat als volgt wordt weergegeven:

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="user_provided_value",​
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1" 
   ```

### Beleid instellen voor FairPlay {#setting-policies-for-fairplay}

U kunt het beleid voor met FairPlay beveiligde inhoud instellen met een machtigingsserver. U kunt uw eigen voorbeeldmachtigingsserver instellen of een door de Adobe verschafte voorbeeldmachtigingsserver gebruiken.

Adobe verstrekt een Server van de Entitlement van de Voorproef ExpressPlay (SEES) die toont hoe te te doen *op tijd gebaseerd* en *apparaatbinding* machtiging. Deze voorbeeldmachtigingsserver is bovenop de ExpressPlay-services gebouwd.

[Referentieserver: Sample ExpressPlay Entitlement Server (SES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

* [Referentieservice: op tijd gebaseerde machtiging](../../multi-drm-workflows/feature-topics/sees-reference-server-time-entitlement.md)
* [Referentieservice: Device-Binding Entitlement](../../multi-drm-workflows/feature-topics/sees-reference-server-binding-entitlement.md)

## Licentie en afspelen voor FairPlay {#licensing-and-playback-for-fairplay}

Voor het verlenen van licenties en het afspelen van door FairPlay beveiligde inhoud moeten URL-schema&#39;s worden gewisseld tussen het schema dat wordt gebruikt in het videomanifestbestand (skd:) en het schema dat wordt gebruikt in ExpressPlay-token-aanvragen (https:).

Hier vindt u instructies voor het implementeren van licenties en het afspelen van een iOS TVSDK-client: [Apple FairPlay inschakelen in TVSDK-toepassingen](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md). U kunt ook desgewenst offline afspelen en licentietrotatie voor FairPlay implementeren.

## HLS offline met FairPlay {#section_047A05D1E3B64883858BC601CFC8F759}

U kunt het gebruikers mogelijk maken om met FairPlay beveiligde inhoud af te spelen wanneer de licentie niet kan worden opgehaald omdat de speler geïsoleerd is van het web (bijvoorbeeld op een vliegtuig).

Download en lees het Apple-document voordat u met deze taak begint **&quot;Offline afspelen met FairPlay Streaming en HTTP Live Streaming&quot;**. Lees de gids om te leren hoe te om de segmenten van de Stroom van het Vervoer (TS) te downloaden en hen te bewaren aan uw lokale machine.

Offline afspelen voor FairPlay implementeren met deze workflow:

1. Download het segment HLS TS.
1. Licentie voor continue huur aanvragen bij de FairPlay-server (zie **&quot;FairPlay Persistent Rental Policy&quot;**).
1. Sla de `persistentContentKey`.
1. De FairPlay-inhoud offline afspelen.

>[!NOTE]
>
>FairPlay Streaming op de client start geen decodering als de blijvende inhoudssleutel is verlopen. Het zal de gebruikerservaring echter voortzetten als de inhoudssleutel tijdens het afspelen verloopt.
>
>Zie [Werken met Live HTTP-streaming](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/HTTPLiveStreaming/HTTPLiveStreaming.html#//apple_ref/doc/uid/TP40016757-CH11-SW3) voor meer informatie.

### FairPlay-licentierotatie {#section_D32AA08C61474B4F876AC2A5F18CB879}

Het roteren van de vergunning is een regeling om vergunningshacking van inhoud te verhinderen die lange tijd speelt.

In een M3U8-manifest wordt elke toetstag toegepast op de volgende TS-segmenten tot de volgende toetstag of tot het einde van het bestand.

Ga als volgt te werk om licentiering toe te voegen:

* Voeg een nieuwe FairPlay-sleuteltag in tijdens de rotatietijd van de licentie.

  U kunt een willekeurig aantal toetstags toevoegen.

  Voor lineaire inhoud zorgt u ervoor dat de meest recente toetstag in het M3U8-venster behouden blijft. iOS zal de volgende M3U8 vragen wanneer er nog ongeveer twee TS-segmenten moeten worden afgespeeld (ongeveer 20 seconden). Als de nieuwe M3U8 nieuwe sleutelcodes bevat, zullen alle belangrijke verzoeken onmiddellijk plaatsvinden. De vorige bestaande toetsen worden niet opnieuw aangevraagd. iOS wacht tot alle belangrijke aanvragen zijn voltooid voordat het afspelen wordt gestart.

  Voor VOD-inhoud met rotatie van de licentie worden alle belangrijke aanvragen afgespeeld.

  Hier volgt een voorbeeld van M3U8 met sleutelrotatie:

  ```
  #EXTM3U
  #EXT-X-TARGETDURATION:10
  #EXT-X-VERSION:5
  #EXT-X-MEDIA-SEQUENCE:0
  #EXT-X-PLAYLIST-TYPE:VOD
  #EXT-X-KEY:METHOD=SAMPLE-AES,URI="skd://one?cek=1dc2cc71d913f4f74eca0c4632
  212b25&iv=e21f0f72b6363ff6143737cb1e9ca8d7",KEYFORMAT="com.apple.streaming
  keydelivery",KEYFORMATVERSIONS="1"
  #EXTINF:10,
  fileSequence0.ts
  #EXTINF:10,
  fileSequence1.ts
  #EXTINF:10,
  fileSequence2.ts
  #EXTINF:10,
  fileSequence3.ts
  #EXTINF:10,
  fileSequence4.ts
  #EXTINF:10,
  fileSequence5.ts
  #EXTINF:10,
  fileSequence6.ts
  #EXTINF:10,
  fileSequence7.ts
  #EXTINF:10,
  #EXT-X-KEY:METHOD=SAMPLE-AES,URI="skd://two?cek=f6efc698b96cf8f4fa46d5237d
  337c77&iv=18401077091784bcda8079acf978dc95",KEYFORMAT="com.apple.streaming
  keydelivery",KEYFORMATVERSIONS="1"
  #EXTINF:10,
  fileSequence8.ts
  #EXTINF:10,
  ```
