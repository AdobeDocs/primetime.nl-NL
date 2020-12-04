---
description: Als u Browser-TVSDK wilt gebruiken, moet u een basisspeler maken en configureren. Voor het afspelen van video-inhoud kunt u op twee manieren een basisspeler maken met de Browser-TVSDK of het UI-framework.
seo-description: Als u Browser-TVSDK wilt gebruiken, moet u een basisspeler maken en configureren. Voor het afspelen van video-inhoud kunt u op twee manieren een basisspeler maken met de Browser-TVSDK of het UI-framework.
seo-title: Basisspeler
title: Basisspeler
uuid: 44a27458-be12-452f-92b9-3cef79439257
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Overzicht {#basic-player-overview}

Als u Browser-TVSDK wilt gebruiken, moet u een basisspeler maken en configureren. Voor het afspelen van video-inhoud kunt u op twee manieren een basisspeler maken: het gebruiken van Browser TVSDK, of het gebruiken van het Kader UI.

## De TVSDK van de browser {#section_4D1C6D4B3A3447DFA2AA0229E140E2D9} gebruiken

Gebruik de API&#39;s van de TVSDK van de browser rechtstreeks om de videospeler te coderen. De SDK biedt u raamwerken en hulpprogramma&#39;s en een referentiespeler waarmee u kunt werken.

>[!TIP]
>
>Als u dit wilt zien werken in een referentiespeler, geeft u geen kenmerken op met `videoDiv`.

## Het UI-framework {#section_AE02384CFEF64A448C108232AB62A9FF} gebruiken

Deze module wordt gebruikt om instanties van de speler tot stand te brengen, waar elke instantie aan een element van het documentobjecten model (DOM) gebonden is dat door de bezoeker wordt verstrekt. Naast het hebben van een geval van Browser TVSDK, bewaart elke spelerinstantie een aantal controles die omhoog het gebruikersinterface voor de speler maken.

De uitvoering van elke controle bestaat uit twee aspecten:

* An `HTMLElement`, which is the visual representation of the component on the screen
* A `Behavior`, die `HTMLElement` beheert en API voor interactie verstrekt

De details over deze controles worden verstrekt aan `VideoPlayer` door een config voorwerp te gebruiken, dat tot de speler bij zijn concretisering wordt overgegaan. Elke component vormt standaard een objecthiërarchie, waarbij het element wordt doorgegeven aan de spelerinstantie aan de basis van de structuur. Wanneer elke component wordt gemaakt, wordt deze op de juiste locatie aan het DOM toegevoegd.

Elke component heeft een naam. Dit is de sleutel in het config-object wanneer het object wordt geregistreerd. De CSS-klasse van het onderliggende DOM-element wordt gevormd als een `vp-`-voorvoegsel dat aan de componentnaam wordt toegevoegd.

Componenten kunnen worden uitgebreid of vervangen, de configuratie ervan kan worden gewijzigd en de initiële eigenschappen kunnen worden ingesteld. Hierdoor hebt u meer controle over API-eigenschappen, de CSS-klassenaam en eventueel aspecten van de implementatie van de component. Deze opties kunnen worden gebruikt om functionaliteit aan te passen en veelvoudige instanties van een component toe te staan die kunnen worden gestileerd of individueel worden gevormd.

Alle componenteninstanties kunnen met het `.behaviors` bezit worden betreden. Exemplaren kunnen worden in- en uitgeschakeld en weergegeven of verborgen. Maar als de instanties eenmaal zijn gemaakt, kunnen deze instanties niet worden verwijderd.
