---
description: U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Adobe.
title: Widevine DRM
exl-id: 44ab032e-e665-4b63-a08b-54e862894987
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Widevine DRM {#widevine-drm}

U kunt de functies van het DRM-systeem (Primetime Digital Rights Management) gebruiken om veilige toegang tot uw video-inhoud te bieden. U kunt ook DRM-oplossingen van derden gebruiken als alternatief voor de geïntegreerde Adobe.

Neem contact op met uw Adobe-vertegenwoordiger voor de meest actuele informatie over de beschikbaarheid van DRM-oplossingen van derden.

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

U kunt de native Widevine DRM van Android gebruiken met HLS CMAF-streams.

>[!NOTE]
>
> Voor Widevine CENC CTR Scheme is minimaal Android-versie 4.4 (API Level 19) vereist.
>
> Voor Widevine CBCS Scheme is minimaal Android versie 7.1 (API Level 25) vereist.

## Gegevens voor licentieserver instellen {#license-server-details}

Bel het volgende `com.adobe.mediacore.drm.DRMManager` API voordat MediaPlayer-bron wordt geladen:

```java
public static void setProtectionData(
String drm,
String licenseServerURL,
Map<String, String> requestProperties)
```

### Argumenten {#arguments-license-server}

* `drm` - `"com.widevine.alpha"` voor Widevine.

* `licenseServerURL` - De URL van de Widevine-licentieserver die licentieaanvragen ontvangt.

* `requestProperties` - Bevat extra kopballen om in het uitgaande vergunningsverzoek te omvatten.

Gebruik bijvoorbeeld de volgende code wanneer u inhoud gebruikt die is verpakt voor Expressplay DRM:

```java
DRMManager.setProtectionData(
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null);
```

## Aangepaste callback opgeven {#custom-callback}

Bel het volgende `com.adobe.mediacore.drm.DRMManager` API voordat MediaPlayer-bron wordt geladen.

```java
public static void setMediaDrmCallback(
MediaDrmCallback callback)
```

### Argumenten {#arguments-custom-callback}

* `callback` - aangepaste implementatie van MediaDRMCallback voor gebruik in plaats van de standaardinstelling `com.adobe.mediacore.drm.WidevineMediaDrmCallback`.

Zie voor meer informatie [Android TVSDK 3.11 API-documentatie](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.11/index.html).

## PSSH-vak van huidige geladen MediaPlayer-bron ophalen {#pssh-box-mediaplayer-resoource}

Bel het volgende `com.adobe.mediacore.drm.DRMManager` API, bij voorkeur in douane callback implementatie.

```java
public static byte[] getPSSH()
```

API keert de Specifieke Dekking van de Kopbal van het Systeem van de Bescherming verbonden aan de geladen media van Windows terug.

Er is een geldig vak beschikbaar voor korte tijd (tussen het maken van DRM-instanties en het laden van sleutels). `MediaDrmCallback callback executeKeyRequest()` U kunt het gebruiken om het halen van vergunningssleutels aan te passen.

>[!NOTE]
>
> `getPSSH()` API wordt alleen ondersteund met één spelerinstantie. Meerdere spelers of de functie instant on moeten serialiseren om het juiste vak te ontvangen.
