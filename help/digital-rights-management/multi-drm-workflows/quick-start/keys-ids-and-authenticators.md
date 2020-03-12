---
description: Om DRM uit te voeren hebt u bepaalde certs en sleutels, met inbegrip van een sleutel van de inhoudsencryptie of CEK nodig om uw inhoud te coderen, een klantenauthenticator voor het beschermen van mededelingen met de servers ExpressPlay, en CEKSIDs voor het identificeren van uw sleutels van de inhoudsencryptie zoals opgeslagen in een zeer belangrijk beheerssysteem.
seo-description: Om DRM uit te voeren hebt u bepaalde certs en sleutels, met inbegrip van een sleutel van de inhoudsencryptie of CEK nodig om uw inhoud te coderen, een klantenauthenticator voor het beschermen van mededelingen met de servers ExpressPlay, en CEKSIDs voor het identificeren van uw sleutels van de inhoudsencryptie zoals opgeslagen in een zeer belangrijk beheerssysteem.
seo-title: Toetsen, id's en Authenticators
title: Toetsen, id's en Authenticators
uuid: 9e5b1a64-b4e9-442f-ac15-26831aaf585d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Toetsen, id&#39;s en Authenticators{#keys-ids-and-authenticators}

Om DRM uit te voeren hebt u bepaalde certs en sleutels, met inbegrip van een sleutel van de inhoudsencryptie of CEK nodig om uw inhoud te coderen, een klantenauthenticator voor het beschermen van mededelingen met de servers ExpressPlay, en CEKSIDs voor het identificeren van uw sleutels van de inhoudsencryptie zoals opgeslagen in een zeer belangrijk beheerssysteem.

U hebt deze items nodig om uw beveiligde inhoud te verpakken, in licentie te geven en af te spelen:

## Inhoudscoderingssleutel {#section_8D16D36BAE3B4D1F92A0C43567D782D0}

De CEK (Content Encryption Key) is een 16-byte tekenreeks die wordt gebruikt voor het versleutelen van inhoud.

**Wat is de CEK?** - De CEK is de sleutel die uw verpakker gebruikt om uw inhoud te coderen. Het is een 16 byte hexadecimale tekenreeks.

**Waar komt de CEK vandaan?** - U (de inhoudsprovider) maakt deze sleutel zelf met een hulpprogramma zoals OpenSSL of Kladblok++. Bijvoorbeeld:

```
openssl rand 16 -hex > cek_hex_file
```

of (voor Adobe Offline Packager):

1. Genereer de hexadecimale tekenreeks van 16 bytes, zoals boven of met een ander gereedschap. Het zal er ongeveer als volgt uitzien:

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Open Kladblok+ en plak in de 16 byte hexreeks.
1. Zet deze waarde van hexadecimale ASCII door Base64-coderend de waarde om uw [!DNL keyfile.bin]tot stand te brengen. (Dit is inbegrepen in [](../../multi-drm-workflows/quick-start/package-your-content.md).)

**Zelfde sleutel, andere naam?** - Ja, u kunt de CEK die door andere namen wordt bedoeld op andere plaatsen zien, zoals:

* ** [!DNL [somefile].bin]* - Adobe Offline Packager noemt de CEK [!DNL [somefile].bin]; Bijvoorbeeld * [!DNL Keyfile.bin]* - Dit is de CEK die door Adobe Offline Packager wordt gebruikt, in de vorm van een bestand op de computer die u gebruikt voor het verpakken van inhoud.

   U &quot;Baseert64&quot;uw willekeurige CEK hexkoord, en bewaart het als dossier (b.v., [!DNL keyfile.bin]), gewoonlijk gevestigd in de [!DNL creds] folder onder [!DNL offlinepkgr/]. In uw het configuratiedossier van Packager (b.v., zou u het kunnen roepen [!DNL widevine.xml] als u voor Widevine DRM verpakt), verwijst u naar uw CEK in uw config- dossier als dit:

   ```
   <config>  
     <in_path>sample.mp4</in_path>  
     <out_type>dash</out_type>
     <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
     […] 
   </config> 
   ```

* **Inhoudssleutel** - U kunt CEK ook zien die als Inhoudssleutel in vraag ( `&contentKey=`), in foutenmeldingen, in steunkaartjes, en in andere documentatie wordt bedoeld.

**Wanneer/waar gebruik ik het?**

1. Ten eerste moet de CEK beschikbaar zijn op de computer waarop u het pakket maakt. Uw verpakkingsprogramma gebruikt uw CEK om uw inhoud te coderen.
1. Ten tweede, moet u CEK in één of andere vorm van het Zeer belangrijke Systeem van het Beheer (KMS) opslaan, met elke CEK verbonden aan zijn eigen Sleutel [van de Encryptie van de](../../multi-drm-workflows/glossary/glossary-cek.md)Inhoud. U kunt uw eigen KMS maken of de Key Storage [van](https://www.expressplay.com/developer/key-storage/)ExpressPlay gebruiken. Hierdoor kan uw winkel (uw machtigingsserver, die de rechten van klanten en de voorziening van de Token van de Vergunning behandelt) een licentietoken voor de klant van KMS trekken gebruikend zeer belangrijke identiteitskaart in plaats van daadwerkelijke CEK (dit is veel veiliger).

## Opslag-id voor coderingssleutel voor inhoud {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

Met de CEKSID (Content Encryption Key Storage ID) wordt de opgeslagen sleutel geïdentificeerd waarmee een gecodeerd stuk video-inhoud wordt gedecodeerd.

**Wat is CEKSID?** - CEKSID is het unieke herkenningsteken voor een Sleutel van de Encryptie van de Inhoud (CEK). De CEK is noodzakelijk om de beschermde inhoud te ontgrendelen; CEKSID is noodzakelijk om tot CEK toegang te hebben van waar het wordt opgeslagen. Wanneer u uw opstelling test, kunt u willekeurige CEKSID en CEK in de tijd van het Pakket verstrekken, zolang u de zelfde informatie voor de vergunning en playbackcontroles gebruikt.

**Waar komt het vandaan?** - U (de inhoudsleverancier) kunt deze identiteitskaart zelf tot stand brengen, of u kunt de dienst zoals de Zeer belangrijke Opslag [van](https://www.expressplay.com/developer/key-storage/) ExpressPlay gebruiken om CEKSIDs voor elk van uw CEKs (en beide op te slaan) te produceren. Verder, kunt u willekeurig geproduceerde CEKSIDs gebruiken, of een regeling aanwenden die uw bedrijfsmodel aanpast. U kunt bijvoorbeeld CEKSID&#39;s gebruiken die betekenisvolle tekenreeksen zijn in plaats van willekeurige hexadecimale tekenreeksen (de id-naam kan bestaan uit onderwerpen, datums, tijden, enz.)

**Wat anders wordt CEKSID genoemd?** - Het wordt soms ook wel een *inhoud-id* genoemd.

## Verificator van klant {#section_F9DDBAA54C544D82A42320CBEEB6CD74}

De authenticator van de klant is een sleutel die u van ExpressPlay krijgt wanneer u daar een beheerdersaccount instelt. De authenticator wordt gebruikt in communicatie met ExpressPlay-servers.

**Wat zijn de klantenauthenticators?** - De twee verificateurs van de klant vormen de twee id&#39;s, één voor testen, één voor productie, die ExpressPlay registreert voor u wanneer u zich aanmeldt bij de service. Deze bestanden zijn altijd beschikbaar op uw ExpressPlay-beheerpagina:
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**Wanneer gebruik ik dit?** - U neemt dit op in alle aanroepen naar ExpressPlay-servers, bijvoorbeeld licentieservers, [ExpressPlay Key Storage](https://www.expressplay.com/developer/key-storage/)en andere aanroepen.
