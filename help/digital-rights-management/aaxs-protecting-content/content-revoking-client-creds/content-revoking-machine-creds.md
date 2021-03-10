---
title: Machinegegevens intrekken
description: Machinegegevens intrekken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Indieningsgegevens machine intrekken{#revoking-machine-credentials}

Adobe houdt een CRL bij voor het intrekken van de referenties van de machine waarvan bekend is dat deze zijn aangetast. Dit CRL wordt automatisch afgedwongen door de SDK. Als er nog meer computers zijn waarvoor u geen licenties wilt laten afgeven op uw licentieserver, kunt u een lijst met machinereferenties maken en de naam en het serienummer van de uitgever van de machinetokens toevoegen die u wilt uitsluiten (gebruik `MachineToken.getMachineTokenId()` om de uitgeversnaam en het serienummer van het machinecertificaat op te halen).

Als u de referenties van een machine intrekt, wordt een `RevocationListFactory`-object gebruikt. Voer de volgende stappen uit om een intrekkingslijst te maken, een bestaande intrekkingslijst te laden en te controleren of een computertoken is ingetrokken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in [De ontwikkelomgeving instellen](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) in uw project.
1. Maak een `ServerCredentialFactory`-instantie om de referenties te laden die nodig zijn voor ondertekening. De referenties van de licentieserver worden gebruikt om de intrekkingslijst te ondertekenen.
1. Maak een `RevocationListFactory`-instantie.
1. Geef de uitgever en het serienummer op van de computertoken die moet worden ingetrokken met een object `IssuerAndSerialNumber`. Alle verzoeken om toegang tot Adobe bevatten een machinetoken.
1. Maak een `RevocationList`-object met het object `IssuerAndSerialNumber` dat u net hebt gemaakt en voeg het object toe aan de intrekkingslijst door het object door te geven naar `RevocationListFactory.addRevocationEntry()`. Genereer de nieuwe intrekkingslijst door `RevocationListFactory.generateRevocationList()` aan te roepen.
1. Als u de intrekkingslijst wilt opslaan, kunt u deze serialiseren door `RevocationList.getBytes()` aan te roepen. Om de lijst te laden, roep `RevocationListFactory.loadRevocationList()` en ga in de geserialiseerde lijst over.
1. Controleer of de handtekening geldig is en de lijst is ondertekend door de juiste licentieserver door `RevocationList.verifySignature()` aan te roepen.
1. Als u wilt controleren of een item is ingetrokken, geeft u het object `IssuerAndSerialNumber` door in `RevocationList.isRevoked()`. De intrekkingslijst kan ook worden doorgegeven aan `HandlerConfiguration` om de SDK de intrekkingslijst voor alle verificatie- en licentieaanvragen te laten afdwingen.

Als u extra items wilt toevoegen aan een bestaande `RevocationList`, laadt u een bestaande intrekkingslijst. Creeer een nieuwe `RevocationListFactory` instantie, en ben zeker om het aantal CRL te verhogen. Roep `RevocationListFactioryEntries.addRevocationEntries` aan om alle ingangen van de oude lijst aan de nieuwe lijst toe te voegen. Vraag `RevocationListFactory.addRevocationEntry` om het even welke nieuwe intrekkingsingangen aan RevocationList toe te voegen.

Zie `com.adobe.flashaccess.samples.revocation.CreateRevocationList` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van Reference Implementation voor voorbeeldcode om te tonen hoe u een intrekkingslijst maakt, een bestaande intrekkingslijst laadt en controleert of een computertoken is ingetrokken.
