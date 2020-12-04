---
description: Terwijl de encryptiemethode AES-128 de volledige container van de vervoerstroom (TS) met inbegrip van kopballen codeert, codeert de encryptie SAMPLE-AES slechts de audio en een deel van de videogegevens.
seo-description: Terwijl de encryptiemethode AES-128 de volledige container van de vervoerstroom (TS) met inbegrip van kopballen codeert, codeert de encryptie SAMPLE-AES slechts de audio en een deel van de videogegevens.
seo-title: Voorbeeld van met AES gecodeerde HLS-streams
title: Voorbeeld van met AES gecodeerde HLS-streams
uuid: 32c1f87b-eb81-4e1c-92ea-ec37260a7ecb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Voorbeeld van met AES gecodeerde HLS-streams{#sample-aes-encrypted-hls-streams}

Terwijl de encryptiemethode AES-128 de volledige container van de vervoerstroom (TS) met inbegrip van kopballen codeert, codeert de encryptie SAMPLE-AES slechts de audio en een deel van de videogegevens.

In gecodeerde streams wordt een beveiligd blok geïdentificeerd waarop het beveiligingsproces is voltooid. H.264 video beschermde blokken zijn het lichaam van types 1 en 5 van de eenheden van de laag van de netwerkaanpassing (NAL). Een beveiligd blok audio is een audioframe en audio moet de AAC-indeling hebben.

>[!IMPORTANT]
>
>U moet over de sleutel en de initialisatievector (IV) beschikken. Browser TVSDK gebruikt de sleutel en IV om de stream te decoderen voordat deze wordt afgespeeld.

Elk beveiligd blok bevat een geheel getal van 16-byte blokken die zijn gecodeerd met de modus AES-128 voor het coderen van codeblokken (CBC) zonder opvulling. CBC vindt plaats in elk beschermd blok, en aan het begin van elk nieuw beschermd blok, moet IV aan zijn originele waarde worden teruggesteld.

De volgende codecs worden ondersteund:

* H.264 wordt ondersteund voor video.
* Voor audio wordt sample-AES alleen ondersteund voor AAC.

