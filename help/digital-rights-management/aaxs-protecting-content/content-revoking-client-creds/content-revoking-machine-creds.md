---
seo-title: Machinegegevens intrekken
title: Machinegegevens intrekken
uuid: 16119ff9-8147-4fe0-9744-a705d94a9400
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Machinegegevens intrekken{#revoking-machine-credentials}

Adobe houdt een CRL bij voor het intrekken van de referenties van computers waarvan bekend is dat ze in gevaar zijn. Dit CRL wordt automatisch afgedwongen door de SDK. Als er nog meer computers zijn waarvoor u geen licenties wilt laten afgeven op uw licentieserver, kunt u een lijst met machinereferenties maken en de naam en het serienummer van de uitgever van de machinetokens toevoegen die u wilt uitsluiten (gebruik `MachineToken.getMachineTokenId()` om de uitgeversnaam en het serienummer van het machinecertificaat op te halen).

Als u de referenties van de machine intrekt, wordt een `RevocationListFactory` object gebruikt. Voer de volgende stappen uit om een intrekkingslijst te maken, een bestaande intrekkingslijst te laden en te controleren of een computertoken is ingetrokken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die in de ontwikkelomgeving [van uw project worden](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) ingesteld.
1. Maak een `ServerCredentialFactory` instantie om de referenties te laden die nodig zijn voor ondertekening. De referenties van de licentieserver worden gebruikt om de intrekkingslijst te ondertekenen.
1. Maak een `RevocationListFactory` instantie.
1. Geef de uitgever en het serienummer op van de computertoken die met een `IssuerAndSerialNumber` object moet worden ingetrokken. Alle Adobe Access-aanvragen bevatten een computertoken.
1. Maak een `RevocationList` object met het zojuist gemaakte `IssuerAndSerialNumber` object en voeg het toe aan de intrekkingslijst door het object door te geven `RevocationListFactory.addRevocationEntry()`. Genereer de nieuwe intrekkingslijst door deze aan te roepen `RevocationListFactory.generateRevocationList()`.
1. Als u de intrekkingslijst wilt opslaan, kunt u deze via serienummering opvragen `RevocationList.getBytes()`. Om de lijst te laden, roep `RevocationListFactory.loadRevocationList()` en ga in de geserialiseerde lijst over.
1. Controleer of de handtekening geldig is en of de lijst is ondertekend door de juiste licentieserver door een aanroep `RevocationList.verifySignature()`.
1. Wanneer u wilt controleren of een item is ingetrokken, geeft u het `IssuerAndSerialNumber` object door `RevocationList.isRevoked()`. De intrekkingslijst kan ook worden doorgegeven `HandlerConfiguration` zodat de SDK de intrekkingslijst voor alle verificatie- en licentieaanvragen afdwingt.

Als u aanvullende items aan een bestaande lijst wilt toevoegen `RevocationList`, laadt u een bestaande intrekkingslijst. Maak een nieuwe `RevocationListFactory` instantie en verhoog het CRL-nummer. Vraag `RevocationListFactioryEntries.addRevocationEntries` om alle ingangen van de oude lijst aan de nieuwe lijst toe te voegen. Vraag `RevocationListFactory.addRevocationEntry` om het even welke nieuwe intrekkingsingangen aan RevocationList toe te voegen.

Zie `com.adobe.flashaccess.samples.revocation.CreateRevocationList` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s voor naslagimplementatie de voorbeeldcode die aangeeft hoe u een intrekkingslijst kunt maken, een bestaande intrekkingslijst laadt en controleert of een machinetoken is ingetrokken.
