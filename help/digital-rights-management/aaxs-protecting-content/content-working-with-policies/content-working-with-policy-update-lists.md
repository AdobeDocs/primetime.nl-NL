---
title: Werken met lijst met beleidsupdates
description: Werken met lijst met beleidsupdates
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Werken met lijst met beleidsupdates{#working-with-policy-update-lists}

Voor licentieservers die geen toegang hebben tot een database voor het opslaan van informatie over beleidsregels, kunt u een lijst met beleidsupdates gebruiken om de licentieserver op de hoogte te stellen van het bijgewerkte beleid. De Lijsten van de Update van het beleid kunnen bijgewerkte versies van beleid of een lijst van beleids IDs bevatten die zijn ingetrokken. Als een lijst met beleidsupdates wordt weergegeven in `HandlerConfiguration`, zal de SDK deze lijst afdwingen bij de afgifte van een licentie.

Het beleid kan ook worden ingetrokken als eigenaren of distributeurs van inhoud de afgifte van licenties in het kader van een bepaald beleid willen stopzetten. Een lijst met beleidsupdates kan worden gebruikt om beleidsherroeping in SDK af te dwingen. De lijsten van de beleidsupdate kunnen ook worden gebruikt om een lijst van bijgewerkt beleid aan SDK te verstrekken. Als u een beleid intrekt, worden reeds afgegeven licenties niet ingetrokken. Het voorkomt alleen dat er in het kader van dat beleid extra vergunningen worden afgegeven.

Wanneer u werkt met een lijst met beleidsupdates, wordt een `PolicyUpdateListFactory` object. Voer de volgende stappen uit om een lijst met beleidsupdates te maken, een bestaande lijst met beleidsupdates te laden en te controleren of een beleid is bijgewerkt of ingetrokken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in de ontwikkelomgeving van uw project.
1. Een `ServerCredentialFactory` -instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Een `PolicyUpdateListFactory` instantie die de `ServerCredential` die u hebt gemaakt.
1. Geef de beleids-id op die moet worden ingetrokken.
1. Een `PolicyRevocationEntry` object dat de beleids-id gebruikt `String` hebt u zojuist gemaakt en toegevoegd aan de lijst met beleidsupdates door deze door te geven `PolicyUpdateListFactory.addRevocationEntry()`. Genereer de nieuwe lijst met beleidsupdates door `PolicyUpdateListFactory.generatePolicyUpdateList()`. Op dezelfde manier kan het bijgewerkte beleid aan de lijst worden toegevoegd gebruikend `PolicyUpdateEntry`.
1. Als er al een lijst met beleidsupdates bestaat, kunt u deze voor het laden serialiseren door `PolicyUpdateList.getBytes()`. Om de lijst te laden, roep `PolicyUpdateListFactory.loadPolicyUpdateList()` en geef de geserialiseerde lijst door.
1. Controleer of de handtekening geldig is en of de lijst is ondertekend door het juiste licentieservercertificaat door het aanroepen van `PolicyUpdateList.verifySignature()`.
1. Om te controleren of een ingang werd ingetrokken, ga beleidsidentiteitskaart over `String` in `PolicyUpdateList.isRevoked()`. De lijst kan ook worden doorgegeven aan `HandlerConfiguration` en de verordening zal worden toegepast bij de afgifte van vergunningen .

Extra items toevoegen aan een bestaande `PolicyUpdateList`, laadt u een bestaande lijst met beleidsupdates. Een nieuwe `PolicyUpdateListFactory` -instantie. P bellen `olicyUpdateListFactory.addEntries` om alle vermeldingen uit de oude lijst toe te voegen aan de nieuwe lijst. Bellen `PolicyUpdateListFactory.addRevocationEntry` of `addUpdatedEntry` om nieuwe intrekkingsingangen toe te voegen of ingangen bij te werken aan PolicyUpdateList.

Voor steekproefcode die toont hoe te om een lijst van beleidsupdate tot stand te brengen, een bestaande lijst van beleidsupdates te laden, en te controleren of een beleid is ingetrokken, zie `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` in de map &quot;samples&quot; van de opdrachtregelprogramma&#39;s van de naslagimplementatie.
