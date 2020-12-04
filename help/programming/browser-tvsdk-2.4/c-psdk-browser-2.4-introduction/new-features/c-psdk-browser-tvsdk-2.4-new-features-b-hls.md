---
description: Browser TVSDK steunt een aantal eigenschappen HLS die u kunt uitvoeren om functionaliteit aan uw videotoepassingen toe te voegen.
seo-description: Browser TVSDK steunt een aantal eigenschappen HLS die u kunt uitvoeren om functionaliteit aan uw videotoepassingen toe te voegen.
seo-title: Ondersteunde HLS-functies
title: Ondersteunde HLS-functies
uuid: 033d81f8-cea4-4687-b2fb-1524d9164d39
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---


# Ondersteunde HLS-functies {#supported-hls-features}

Browser TVSDK steunt een aantal eigenschappen HLS die u kunt uitvoeren om functionaliteit aan uw videotoepassingen toe te voegen.

* [HLS Core-afspelen](#hls-core-playback)
* [HLS Geavanceerde afspeelfuncties](#hls-advanced-playback)
* [Functies voor beveiliging van HLS-inhoud](#hls-content-protection)
* [HLS Core- en invoegfuncties](#hls-core-ad-insertion)
* [HLS Geavanceerde functies voor het invoegen van afbeeldingen](#hls-advanced-ad-insertion)
* [HLS-integratie](#hls-integrations)

>[!TIP]
>
>In de lijsten van de eigenschapmatrijs hieronder, ![gesteund pictogram](assets/supported15.png) betekent dat de eigenschap in de huidige versie wordt gesteund.

>[!TIP]
>
>In de kolom &quot;Beperking van Platform&quot; in Safari staat dat het gebruiksgeval niet wordt ondersteund omdat dat platform geen ondersteuning voor het platform toestaat. Gebruik SSAI in geval van invoeging. Als er voor u belangrijke afspeelbeperkingen zijn, forceert u de fallback naar Flash op Safari totdat het platform ondersteuning biedt voor het gebruik van de invoegtoepassing.

<!--<a id="section_9FB9193D5763448CB228B96164661738"></a>-->

De volgende functies worden ondersteund:

<!-- 

Removed Nielsen row 
<table id="table_D9E2D82992554905A0A551CC71AFA189"> 
 <title>HLS integrations</title> 
 <tgroup cols="6"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col4" colwidth="*" /> 
  <colspec colnum="5" colname="col5" colwidth="*" /> 
  <colspec colnum="6" colname="col7" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" morerows="1" class="entry"> Category </th> 
    <th colname="col2" morerows="1" class="entry"> Content type </th> 
    <th colname="col3" morerows="1" class="entry"> Feature </th> 
    <th colname="col4" morerows="1" class="entry"> Flash </th> 
    <th namest="col5" nameend="col7" class="entry"> HTML5 </th> 
   </tr> 
   <tr> 
    <th colname="col5" class="entry"> FF, IE, Chrome, Android Chrome </th> 
    <th colname="col7" class="entry"> Safari, iOS Safari </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## HLS-integratie {#hls-integrations}

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Integraties | VOD + Live | Adobe Analytics VHL-integratie | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |

## Geavanceerde HLS-invoegfuncties (CSAI) {#hls-advanced-ad-insertion}

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD | Alleen advertentie | Niet ondersteund | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Ad Insertion | VOD + Live | Doelparameters | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Ad Insertion | VOD + Live | Aangepast advertentiebeleid | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Ad Insertion | VOD + Live | Lazy en laden | ![ondersteund pictogram](assets/supported15.png) | Niet ondersteund | Beperking van Platform |
| Ad Insertion | VOD | Companion-advertenties, banneradvertenties en aanklikbare advertenties | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Ad Insertion | VOD | VPAID 2.0 | SWF | JavaScript | JavaScript |

## HLS-core en invoegfuncties (CSAI) {#hls-core-ad-insertion}

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD + Live | Pre-roll | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Ad Insertion | VOD + Live | Midden rol | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Ad Insertion | VOD + Live | Na de rol | Alleen VOD | Alleen VOD | Alleen VOD |
| Ad Insertion | FER VOD | Resolutie en gedrag toevoegen | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Ad Insertion | VOD + Live | Standaardbeleid en standaardbeleid | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Ad Insertion | VOD + Live | VAST 2,0/3,0 | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Ad Insertion | VOD + Live | VMAP 1.0 | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Ad Insertion | VOD + Live | CRS v3.1 | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |

## Functies voor HLS-inhoudsbeveiliging {#hls-content-protection}

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Inhoud beschermen | VOD + Live | AES-128 | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Inhoud beschermen | VOD + Live | Sample-AES | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Inhoud beschermen | VOD | DRM | Adobe Access | Niet ondersteund | FairPlay |

## Geavanceerde HLS-afspeelfuncties {#hls-advanced-playback}

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Afspelen | VOD | Afspelen bij verschuiving | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD | Alleen audio afspelen | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD | Steen spelen | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD | Gladde truc | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Afspelen | VOD + Live | ID3-parsering | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Niet ondersteund |
| Afspelen | VOD + Live | Ondersteuning van discontinue markeertekens | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD + Live | Verwarmde stromen | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Afspelen | VOD + Live | Facturering | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD + Live | Bladeren | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |

## Afspelen van HLS-core {#hls-core-playback}

| Categorie | Inhoudstype | Functie | Flash | HTML5: FF, IE, Chrome, Android-chroom | HTML5: Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Afspelen | VOD + Live | Algemeen afspelen (Afspelen, Pauzeren, Zoeken) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | FER VOD | Algemeen afspelen (Afspelen, Pauzeren, Zoeken) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD + Live | Adaptieve bitsnelheid | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD + Live | 608/708 bijschriften | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD + Live | WebVTT | ![ondersteund pictogram](assets/supported15.png) | Alleen VOD | Alleen VOD |
| Afspelen | VOD + Live | Kennelijke failover | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) |
| Afspelen | VOD + Live | Geavanceerde failover | ![ondersteund pictogram](assets/supported15.png) | Alleen VOD | Beperking van Platform |
| Afspelen | VOD + Live | QoS- en spelersmeldingen | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperkte QoS-ondersteuning |
| Afspelen | VOD + Live | Ondersteuning voor cookie headers | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Afspelen | VOD + Live | Parameters voor bufferbesturing instellen | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Afspelen | VOD + Live | Aangepaste besturingselementen voor bitsnelheid instellen | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Afspelen | VOD + Live | Aangepaste tags | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Afspelen | VOD + Live | Geluid met late binding | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |
| Afspelen | VOD + Live | 302 omleiding | ![ondersteund pictogram](assets/supported15.png) | ![ondersteund pictogram](assets/supported15.png) | Beperking van Platform |