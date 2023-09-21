---
description: Om DRM uit te voeren hebt u bepaalde certs en sleutels, met inbegrip van een sleutel van de inhoudsencryptie of CEK nodig om uw inhoud te coderen, een klantenauthenticator voor het beschermen van mededelingen met de servers ExpressPlay, en CEKSIDs voor het identificeren van uw sleutels van de inhoudsencryptie zoals opgeslagen in een zeer belangrijk beheerssysteem.
title: Toetsen, id's en Authenticators
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

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

of (voor de Adobe Offline Packager):

1. Genereer de hexadecimale tekenreeks van 16 bytes, zoals boven of met een ander gereedschap. Het zal er ongeveer als volgt uitzien:

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Open Kladblok+ en plak in de 16 byte hexreeks.
1. Zet deze waarde van hexuitdraai ASCII door Base64-coderend de waarde om tot uw [!DNL keyfile.bin]. (Dit valt onder [](../../multi-drm-workflows/quick-start/package-your-content.md).)

**Zelfde sleutel, andere naam?** - Ja, u kunt de CEK die door andere namen wordt bedoeld op andere plaatsen zien, zoals:

* ** [!DNL [somfiel].bin]** - De Adobe Offline Packager verwijst naar CEK als [!DNL [somfiel].bin]; bijvoorbeeld * [!DNL Keyfile.bin]* - Dit is de CEK die door de Adobe Offline Packager wordt gebruikt, in de vorm van een bestand op de computer die u gebruikt voor het verpakken van inhoud.

  U &quot;Base64&quot;uw willekeurige CEK hexreeks, en bewaart het als dossier (b.v., [!DNL keyfile.bin]), meestal in de [!DNL creds] directory onder [!DNL offlinepkgr/]. In uw Packager config- dossier (b.v., zou u het kunnen roepen [!DNL widevine.xml] als u voor Widevine DRM) verpakt, verwijst u naar uw CEK in uw configdossier als dit:

  ```
  <config>  
    <in_path>sample.mp4</in_path>  
    <out_type>dash</out_type>
    <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
    […] 
  </config> 
  ```

* **Inhoudssleutel** - U kunt CEK ook zien die als Inhoudssleutel in vraag wordt bedoeld ( `&contentKey=`), in foutberichten, in ondersteuningstickets en in andere documentatie.

**Wanneer/waar gebruik ik het?**

1. Ten eerste moet de CEK beschikbaar zijn op de computer waarop u het pakket maakt. Uw verpakkingsprogramma gebruikt uw CEK om uw inhoud te coderen.
1. Ten tweede, moet u CEK in één of andere vorm van Zeer belangrijk Systeem van het Beheer (KMS) opslaan, met elke CEK verbonden aan zijn [Inhoudscoderingssleutel](../../multi-drm-workflows/glossary/glossary-cek.md). U kunt uw eigen KMS maken of [Belangrijke opslag van ExpressPlay](https://www.expressplay.com/developer/key-storage/). Hierdoor kan uw winkel (uw machtigingsserver, die de rechten van klanten en de voorziening van de Token van de Vergunning behandelt) een licentietoken voor de klant van KMS trekken gebruikend zeer belangrijke identiteitskaart in plaats van daadwerkelijke CEK (dit is veel veiliger).

## Opslag-id voor coderingssleutel voor inhoud {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

Met de CEKSID (Content Encryption Key Storage ID) wordt de opgeslagen sleutel geïdentificeerd waarmee een gecodeerd stuk video-inhoud wordt gedecodeerd.

**Wat is CEKSID?** - CEKSID is het unieke herkenningsteken voor een Sleutel van de Encryptie van de Inhoud (CEK). CEK is noodzakelijk om de beschermde inhoud te ontgrendelen; CEKSID is noodzakelijk om tot CEK toegang te hebben van waar het wordt opgeslagen. Wanneer u uw opstelling test, kunt u willekeurige CEKSID en CEK in de tijd van het Pakket verstrekken, zolang u de zelfde informatie voor de vergunning en playbackcontroles gebruikt.

**Waar komt het vandaan?** - U (de inhoudprovider) kunt deze id zelf maken, of u kunt een service zoals [Belangrijke opslag van ExpressPlay](https://www.expressplay.com/developer/key-storage/) om CEKSIDs voor elk van uw CEKs (te produceren en beide op te slaan). Verder, kunt u willekeurig geproduceerde CEKSIDs gebruiken, of een regeling aanwenden die uw bedrijfsmodel aanpast. U kunt bijvoorbeeld CEKSID&#39;s gebruiken die betekenisvolle tekenreeksen zijn in plaats van willekeurige hexadecimale tekenreeksen (de id-naam kan bestaan uit onderwerpen, datums, tijden, enz.)

**Wat anders wordt CEKSID genoemd?** - Het wordt soms aangeduid als een *Inhoud-id*.

## Verificator van klant {#section_F9DDBAA54C544D82A42320CBEEB6CD74}

De authenticator van de klant is een sleutel die u van ExpressPlay krijgt wanneer u daar een beheerdersaccount instelt. De authenticator wordt gebruikt in communicatie met ExpressPlay-servers.

**Wat zijn de klantenauthenticators?** - De twee verificateurs van de klant vormen de twee id&#39;s, één voor testen, één voor productie, die ExpressPlay registreert voor u wanneer u zich aanmeldt bij de service. Deze bestanden zijn altijd beschikbaar op uw ExpressPlay-beheerpagina:
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**Wanneer gebruik ik dit?** - U neemt dit op in alle aanroepen naar ExpressPlay-servers, bijvoorbeeld licentieservers, [ExpressPlay-sleutelopslag](https://www.expressplay.com/developer/key-storage/), en andere vraag.
