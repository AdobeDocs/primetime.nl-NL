---
description: Als u Browser-TVSDK wilt gebruiken, moet u een basisspeler maken en configureren. Voor het afspelen van video-inhoud kunt u op twee manieren een basisspeler maken met de Browser-TVSDK of het UI-framework.
title: Basisspeler
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Overzicht {#basic-player-overview}

Als u Browser-TVSDK wilt gebruiken, moet u een basisspeler maken en configureren. Voor het afspelen van video-inhoud kunt u op twee manieren een basisspeler maken: met de Browser-TVSDK of via het UI-framework.

## De TVSDK van de browser gebruiken {#section_4D1C6D4B3A3447DFA2AA0229E140E2D9}

Gebruik de API&#39;s van de TVSDK van de browser rechtstreeks om uw videospeler te coderen. De SDK biedt u raamwerken en hulpprogramma&#39;s en een referentiespeler waarmee u kunt werken.

>[!TIP]
>
>Geef geen kenmerken op met `videoDiv`.

## Het UI-framework gebruiken {#section_AE02384CFEF64A448C108232AB62A9FF}

Deze module wordt gebruikt om instanties van de speler tot stand te brengen, waar elke instantie aan een element van het documentobjecten model (DOM) gebonden is dat door de bezoeker wordt verstrekt. Naast het hebben van een geval van Browser TVSDK, bewaart elke spelerinstantie een aantal controles die omhoog het gebruikersinterface voor de speler maken.

De uitvoering van elke controle bestaat uit twee aspecten:

* An `HTMLElement`, de visuele weergave van de component op het scherm
* A `Behavior`, die de `HTMLElement` en biedt een API voor interacties

De details over deze controles worden verstrekt aan de `VideoPlayer` door een config-object te gebruiken, dat bij de instantie aan de speler wordt doorgegeven. Elke component vormt standaard een objecthiërarchie, waarbij het element wordt doorgegeven aan de spelerinstantie aan de basis van de structuur. Wanneer elke component wordt gemaakt, wordt deze op de juiste locatie aan het DOM toegevoegd.

Elke component heeft een naam. Dit is de sleutel in het config-object wanneer het object wordt geregistreerd. De CSS-klasse van het onderliggende DOM-element wordt gevormd als een `vp-` voorvoegsel dat aan de componentnaam wordt toegevoegd.

Componenten kunnen worden uitgebreid of vervangen, de configuratie ervan kan worden gewijzigd en de initiële eigenschappen kunnen worden ingesteld. Hierdoor hebt u meer controle over API-eigenschappen, de CSS-klassenaam en eventueel aspecten van de implementatie van de component. Deze opties kunnen worden gebruikt om functionaliteit aan te passen en veelvoudige instanties van een component toe te staan die kunnen worden gestileerd of individueel worden gevormd.

Alle componentinstanties zijn toegankelijk met de `.behaviors` eigenschap. Exemplaren kunnen worden in- en uitgeschakeld en weergegeven of verborgen. Maar als de instanties eenmaal zijn gemaakt, kunnen deze instanties niet worden verwijderd.
