---
title: Machinegegevens intrekken
description: Machinegegevens intrekken
copied-description: true
exl-id: 4f49a94c-1bd9-4a7a-ac92-4da0b7fe4ae4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Machinegegevens intrekken {#revoking-machine-credentials}

Adobe houdt een CRL bij voor het intrekken van de referenties van de machine waarvan bekend is dat deze zijn aangetast. Dit CRL wordt automatisch afgedwongen door de SDK. Als er nog meer machines zijn waarvoor u geen licenties wilt laten afgeven op de licentieserver, kunt u een lijst met machinereferenties maken en de naam en het serienummer van de uitgever toevoegen van de computertokens die u wilt uitsluiten (gebruik `MachineToken.getMachineTokenId()` om de uitgeversnaam en het serienummer van het machinecertificaat op te halen).

Als u de computergegevens intrekt, wordt een `RevocationListFactory` object. Voer de volgende stappen uit om een intrekkingslijst te maken, een bestaande intrekkingslijst te laden en te controleren of een computertoken is ingetrokken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die in [De ontwikkelomgeving instellen](../../protecting-content/setting-up-the-sdk/setup-dev-env.md) in uw project.
1. Een `ServerCredentialFactory` -instantie om de referenties te laden die nodig zijn voor ondertekening. De referenties van de licentieserver worden gebruikt om de intrekkingslijst te ondertekenen.
1. Een `RevocationListFactory` -instantie.
1. Geef de uitgever en het serienummer op van het computertoken dat moet worden ingetrokken met behulp van een `IssuerAndSerialNumber` object. Alle Adobe Primetime DRM-aanvragen bevatten een computertoken.
1. Een `RevocationList` object gebruiken `IssuerAndSerialNumber` zojuist gemaakte object en voeg het toe aan de intrekkingslijst door het door te geven `RevocationListFactory.addRevocationEntry()`. Genereer de nieuwe intrekkingslijst door `RevocationListFactory.generateRevocationList()`.

1. Als u de intrekkingslijst wilt opslaan, kunt u deze via serienummering opslaan door `RevocationList.getBytes()`. Om de lijst te laden, roep `RevocationListFactory.loadRevocationList()` en geef de geserialiseerde lijst door.

1. Controleer of de handtekening geldig is en de lijst is ondertekend door de juiste licentieserver door een aanroep van `RevocationList.verifySignature()`.
1. Om te controleren of een ingang werd ingetrokken, ga over `IssuerAndSerialNumber` object in `RevocationList.isRevoked()`. De intrekkingslijst kan ook worden doorgegeven aan `HandlerConfiguration` om de SDK de intrekkingslijst voor alle verificatie- en licentieaanvragen te laten afdwingen.

Extra items toevoegen aan een bestaande `RevocationList`, laadt u een bestaande intrekkingslijst. Een nieuwe `RevocationListFactory` en zorg ervoor dat u het CRL-nummer verhoogt. Bellen `RevocationListFactioryEntries.addRevocationEntries` om alle vermeldingen uit de oude lijst toe te voegen aan de nieuwe lijst. Bellen `RevocationListFactory.addRevocationEntry` om nieuwe intrekkingsitems toe te voegen aan de RevocationList.

Voor voorbeeldcode die toont hoe u een intrekkingslijst maakt, een bestaande intrekkingslijst laadt en controleert of een machinetoken is ingetrokken, raadpleegt u `com.adobe.flashaccess.samples.revocation.CreateRevocationList` in de opdrachtregelprogramma&#39;s voor de referentieimplementatie [!DNL samples] directory.
