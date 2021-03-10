---
description: Browser TVSDK steunt een aantal eigenschappen DASH die u kunt uitvoeren om functionaliteit aan uw videotoepassingen toe te voegen.
title: Ondersteunde DASH-functies
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---


# Ondersteunde DASH-functies{#supported-dash-features}

Browser TVSDK steunt een aantal eigenschappen DASH die u kunt uitvoeren om functionaliteit aan uw videotoepassingen toe te voegen.

* [DASH Core-afspeelfuncties](#dash-core-playback)
* [Geavanceerde afspeelfuncties DASH](#dash-advanced-playback)
* [Functies voor DASH-inhoudsbeveiliging](#dash-content-protection)
* [DASH Core- en invoegfuncties](#dash-core-ad-insertion)
* [Geavanceerde DASH-functies en invoegfuncties](#dash-advanced-insertion-features)
* [DASH-integratie](#dash-integrations)

>[!TIP]
>
>In de onderstaande tabel met functiematrix ![](assets/supported15.png)
>betekent dat de functie wordt ondersteund in de huidige release.

De volgende functies worden ondersteund:

<!-- 

<table id="table_lrb_p2g_xx"> 
 <title>DASH integrations</title> 
 <tgroup cols="4"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col6" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" class="entry"> Category </th> 
    <th colname="col2" class="entry"> Content type </th> 
    <th colname="col3" class="entry"> Feature </th> 
    <th colname="col6" align="center" class="entry"> 
     <lines>
       HTML5 FF, IE, Chrome, Android Chrome
     </lines> </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_14D9248BD1D8410E83AD27DB4AB3B6ED" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_EFA853CB763446B3B37F2CF6BCC53EE1" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Billing </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_B3A4E5937CEC4052977C08767219BC2B" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Browserify </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_3330E81B86C84AD391AEBFDFE911A47F" /> </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## DASH-integratie {#dash-integrations}

| Categorie | Inhoudstype | Functie | HTML5 FF, IE, Chrome, Android-chroom |
|---|---|---|---|
| Integraties | VOD + Live | Adobe Analytics VHL-integratie | ![](assets/supported15.png) |
| Integraties | VOD + Live | Facturering | ![](assets/supported15.png) |
| Integraties | VOD + Live | Bladeren | ![](assets/supported15.png) |

## Geavanceerde DASH-invoegfuncties (CSAI) {#dash-advanced-insertion-features}

| Categorie | Inhoudstype | Functie | HTML5 FF, IE, Chrome, Android-chroom |
|---|---|---|---|
| Ad Insertion | VOD | Alleen advertentie | Niet ondersteund |
| Ad Insertion | VOD | Doelparameters | Alleen VOD |
| Ad Insertion | VOD | Aangepaste parameters | Alleen VOD |
| Ad Insertion | VOD + Live | Aangepast advertentiebeleid | Niet ondersteund |
| Ad Insertion | VOD + Live | Lazy en laden | Niet ondersteund |
| Ad Insertion | VOD | Companion-advertenties, banneradvertenties en aanklikbare advertenties | Niet ondersteund |
| Ad Insertion | VOD | VPAID 2.0 | Niet ondersteund |

## DASH-core en invoegfuncties (CSAI) {#dash-core-ad-insertion}

| Categorie | Inhoudstype | Functie | HTML5 FF, IE, Chrome, Android-chroom |
|---|---|---|---|
| Ad Insertion | VOD + Live | Pre-roll | Alleen VOD |
| Ad Insertion | VOD + Live | Midden rol | Alleen VOD |
| Ad Insertion | VOD + Live | Na de rol | Alleen VOD |
| Ad Insertion | FER VOD | Resolutie en gedrag toevoegen | Niet ondersteund |
| Ad Insertion | VOD + Live | Standaardbeleid en standaardbeleid | Alleen VOD |
| Ad Insertion | VOD + Live | VAST 2,0/3,0 | Alleen VOD |
| Ad Insertion | VOD + Live | VMAP 1.0 | Alleen VOD |
| Ad Insertion | VOD + Live | CRS v3.1 | Alleen VOD |

## Beveiligingsfuncties voor DASH-inhoud {#dash-content-protection}

<table id="table_hrb_p2g_xx">  
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Categorie </th> 
   <th colname="col2" class="entry"> Inhoudstype </th> 
   <th colname="col3" class="entry"> Functie </th> 
   <th colname="col6" class="entry"> HTML5 FF, IE, Chrome, Android-chroom</th>
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Inhoud beschermen </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> AES-128 </td> 
   <td colname="col6"> Niet ondersteund </td>
  </tr> 
  <tr> 
   <td colname="col1"> Inhoud beschermen </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> Sample-AES </td> 
   <td colname="col6"> Niet ondersteund </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Inhoud beschermen </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3"> DRM </td> 
   <td colname="col6"> 
    <ul id="ul_irb_p2g_xx"> 
     <li id="li_C4643F2978BC4C8ABDB3E6C72C75A468">Widevine on 
      <ul id="ul_7047EA49AA3F40FE8F90E0ED6C028D83"> 
       <li id="li_B575735388D74D789D56BF373A470A6D">Chroom </li> 
       <li id="li_855146E4AC3A48E69B65F0022E1C0156">Firefox 47+ </li> 
       <li id="li_BC06B0A6EAAC4FC991C713775A8BB4DA">Chromecast </li> 
      </ul> </li> 
     <li id="li_D48B51C2208F423CB85D08886C2E1C66">PlayReady in Internet Explorer op Windows 8.1 en Edge </li> 
     <li id="li_2786AC19387241A296E015EE6FD07F2D">Adobe Access voor Windows Firefox (alleen video) </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Geavanceerde afspeelfuncties in DASH {#dash-advanced-playback}

| Categorie | Inhoudstype | Functie | HTML5, FF, IE, Chrome, Android-chroom |
|---|---|---|---|
| Afspelen | VOD | Afspelen bij verschuiving | ![](assets/supported15.png) |
| Afspelen | VOD | Alleen-audio afspelen | ![](assets/supported15.png) |
| Afspelen | VOD | Steen spelen | ![](assets/supported15.png) |
| Afspelen | VOD | Vloeiende steen afspelen | ![](assets/supported15.png) |
| Afspelen | VOD + Live | ID3-parsering | Niet ondersteund |
| Afspelen | VOD | Ondersteuning voor meerdere perioden | Alleen VOD |
| Afspelen | VOD + Live | Verwarmde stromen | Niet ondersteund |
| Afspelen | VOD + Live | Facturering | ![](assets/supported15.png) |
| Afspelen | VOD + Live | Bladeren | ![](assets/supported15.png) |

## DASH core playback features {#dash-core-playback}

| Categorie | Inhoudstype | Functie | HTML5 FF, IE, Chrome, Android-chroom |
|---|---|---|---|
| Afspelen | VOD + Live | Algemeen afspelen (Afspelen, Pauzeren, Zoeken) | ![](assets/supported15.png) |
| Afspelen | FER VOD | Algemeen afspelen (Afspelen, Pauzeren, Zoeken) | Niet ondersteund |
| Afspelen | VOD + Live | Adaptieve bitsnelheid | ![](assets/supported15.png) |
| Afspelen | VOD + Live | 608/708 bijschriften | ![](assets/supported15.png) |
| Afspelen | VOD + Live | WebVTT | Alleen VOD |
| Afspelen | VOD + Live | Failover | Alleen VOD |
| Afspelen | VOD + Live | QoS- en Player-meldingen | ![](assets/supported15.png) |
| Afspelen | VOD + Live | Ondersteuning voor cookie headers | ![](assets/supported15.png) |
| Afspelen | VOD + Live | Parameters voor bufferbesturing instellen | ![](assets/supported15.png) |
| Afspelen | VOD + Live | Aangepaste besturingselementen voor bitsnelheid instellen | ![](assets/supported15.png) |
| Afspelen | VOD + Live | Aangepaste tags (EventStream) | Alleen VOD (inline) |
| Afspelen | VOD + Live | Geluid met late binding | Alleen VOD |
| Afspelen | VOD + Live | 302 omleiding | Alleen VOD |