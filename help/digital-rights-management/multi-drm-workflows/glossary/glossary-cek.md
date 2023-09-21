---
title: Verklarende woordenlijst
description: Veelgebruikte termen die speciale definitie vereisen.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Verklarende woordenlijst {#glossary}

Veelgebruikte termen die speciale definitie vereisen.

## Inhoudscoderingssleutel {#content-encryption-key}

De door een hulpprogramma gegenereerde coderingssleutel voor inhoud (CEK) wordt vervolgens door een inhoudsverpakker gebruikt bij het voorbereiden van inhoud die moet worden beveiligd.
Het nut produceert de sleutel in hexuitdraai met een lengte van 16 bytes.
Deze gids toont, in nota&#39;s en foutenmelding, dossier, en bevelsteekproeven, de volgende varianten van parameternamen en waardenamen voor CEK:

* inhoudssleutel
* `&contentKey=`
* `?cek=`
* `<CEK>`
* `[YOUR CONTENT KEY]`

Bestandsnamen voor een CEK worden weergegeven als:

* `keyfile.bin`
* `creds/fairplaybin`
* `Jaigo_DASH/_info/key.B64.random`

CEK zelf kan in een zeer belangrijk beheerssysteem worden opgeslagen evenals worden gecodeerd. Deze gids verwijst naar de opslagindex als CEKSID van de Opslag CEK. De term Key Encryption Key (KEK) verwijst naar de coderingssleutel op het tweede niveau en naar de term `ek` verwijst naar de waarde van die encryptie.
Sommige vraag gebruikt zowel CEK als identiteitskaart CEKSID van de Opslag CEK, en CEK die van opslag wordt teruggewonnen moet CEK aanpassen die in de vraag wordt verstrekt.
Voor HLS Offline met FairPlay is er ook een `persistentContentKey` die kunnen worden ingesteld op verlopen.

## Opslag-id voor coderingssleutel voor inhoud {#content-encryption-key-storage-id}

De CEKSID (Content Encryption Key Storage ID) is een id voor het ophalen van een Content Encryption Key van een sleutelbeheersysteem.

CEKSID wordt ook bedoeld als
* Sleutel-id
* Inhoud-id
* `&kid`

## Verificator van klant {#customer-authenticator}

Een sleutel voor authentificatie in verzoeken aan API van Uitdrukking. Aanvragen kunnen verzoeken om tokens bevatten.
