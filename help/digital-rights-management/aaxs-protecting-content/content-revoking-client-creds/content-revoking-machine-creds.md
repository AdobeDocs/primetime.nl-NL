---
title: Machinegegevens intrekken
description: Machinegegevens intrekken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Machinegegevens intrekken{#revoking-machine-credentials}

Adobe houdt een CRL bij voor het intrekken van de referenties van de machine waarvan bekend is dat deze zijn aangetast. Dit CRL wordt automatisch afgedwongen door de SDK. Als er nog meer machines zijn waarvoor u geen licenties wilt laten afgeven op de licentieserver, kunt u een lijst met machinereferenties maken en de naam en het serienummer van de uitgever toevoegen van de computertokens die u wilt uitsluiten (gebruik `MachineToken.getMachineTokenId()` om de uitgeversnaam en het serienummer van het machinecertificaat op te halen).

Als u de computergegevens intrekt, wordt een `RevocationListFactory` object. Voer de volgende stappen uit om een intrekkingslijst te maken, een bestaande intrekkingslijst te laden en te controleren of een computertoken is ingetrokken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in [De ontwikkelomgeving instellen](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in uw project.
1. Een `ServerCredentialFactory` -instantie om de referenties te laden die nodig zijn voor ondertekening. De referenties van de licentieserver worden gebruikt om de intrekkingslijst te ondertekenen.
1. Een `RevocationListFactory` -instantie.
1. Geef de uitgever en het serienummer op van het computertoken dat moet worden ingetrokken met behulp van een `IssuerAndSerialNumber` object. Alle verzoeken van de Toegang van de Adobe bevatten een machinetoken.
1. Een `RevocationList` object gebruiken `IssuerAndSerialNumber` zojuist gemaakte object en voeg het toe aan de intrekkingslijst door het door te geven `RevocationListFactory.addRevocationEntry()`. Genereer de nieuwe intrekkingslijst door `RevocationListFactory.generateRevocationList()`.
1. Als u de intrekkingslijst wilt opslaan, kunt u deze via serienummering opslaan door `RevocationList.getBytes()`. Om de lijst te laden, roep `RevocationListFactory.loadRevocationList()` en geef de geserialiseerde lijst door.
1. Controleer of de handtekening geldig is en de lijst is ondertekend door de juiste licentieserver door een aanroep van `RevocationList.verifySignature()`.
1. Om te controleren of een ingang werd ingetrokken, ga over `IssuerAndSerialNumber` object in `RevocationList.isRevoked()`. De intrekkingslijst kan ook worden doorgegeven aan `HandlerConfiguration` de SDK de intrekkingslijst voor alle verificatie- en licentieaanvragen laten afdwingen.

Extra items toevoegen aan een bestaande `RevocationList`, een bestaande intrekkingslijst laden. Een nieuwe `RevocationListFactory` en zorg ervoor dat u het CRL-nummer verhoogt. Bellen `RevocationListFactioryEntries.addRevocationEntries` om alle vermeldingen uit de oude lijst toe te voegen aan de nieuwe lijst. Bellen `RevocationListFactory.addRevocationEntry` om nieuwe intrekkingsitems toe te voegen aan de RevocationList.

Voor voorbeeldcode die toont hoe u een intrekkingslijst maakt, een bestaande intrekkingslijst laadt en controleert of een machinetoken is ingetrokken, raadpleegt u `com.adobe.flashaccess.samples.revocation.CreateRevocationList` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie.
