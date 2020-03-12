---
seo-title: Werken met lijst met beleidsupdates
title: Werken met lijst met beleidsupdates
uuid: 583abb31-5c80-43f2-bc3d-a2300f61c4ea
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Werken met lijst met beleidsupdates{#working-with-policy-update-lists}

Voor licentieservers die geen toegang hebben tot een database voor het opslaan van informatie over beleidsregels, kunt u een lijst met beleidsupdates gebruiken om de licentieserver op de hoogte te stellen van het bijgewerkte beleid. De Lijsten van de Update van het beleid kunnen bijgewerkte versies van beleid of een lijst van beleids IDs bevatten die zijn ingetrokken. Als er een lijst met beleidsupdates wordt weergegeven in `HandlerConfiguration`, dwingt de SDK deze lijst af bij het uitgeven van een licentie.

Het beleid kan ook worden ingetrokken als eigenaren of distributeurs van inhoud de afgifte van licenties in het kader van een bepaald beleid willen stopzetten. Een lijst met beleidsupdates kan worden gebruikt om beleidsherroeping in SDK af te dwingen. De lijsten van de beleidsupdate kunnen ook worden gebruikt om een lijst van bijgewerkt beleid aan SDK te verstrekken. Als u een beleid intrekt, worden reeds afgegeven licenties niet ingetrokken. Het voorkomt alleen dat er in het kader van dat beleid extra vergunningen worden afgegeven.

Bij het werken met de lijst met beleidsupdates wordt een `PolicyUpdateListFactory` object gebruikt. Voer de volgende stappen uit om een lijst met beleidsupdates te maken, een bestaande lijst met beleidsupdates te laden en te controleren of een beleid is bijgewerkt of ingetrokken met de Java API:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden vermeld in de ontwikkelomgeving van uw project.
1. Maak een `ServerCredentialFactory` instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Maak een `PolicyUpdateListFactory` instantie met de `ServerCredential` instantie die u hebt gemaakt.
1. Geef de beleids-id op die moet worden ingetrokken.
1. Maak een `PolicyRevocationEntry` object met de beleids-id die `String` u net hebt gemaakt en voeg het toe aan de lijst met beleidsupdates door het object door te geven `PolicyUpdateListFactory.addRevocationEntry()`. Genereer de nieuwe lijst met beleidsupdates door deze aan te roepen `PolicyUpdateListFactory.generatePolicyUpdateList()`. Op dezelfde manier kan het bijgewerkte beleid aan de lijst worden toegevoegd gebruikend `PolicyUpdateEntry`.
1. Als er al een lijst met beleidsupdates bestaat, kunt u deze voor het laden serialiseren door een aanroep te doen `PolicyUpdateList.getBytes()`. Om de lijst te laden, roep `PolicyUpdateListFactory.loadPolicyUpdateList()` en ga in de geserialiseerde lijst over.
1. Controleer of de handtekening geldig is en of de lijst is ondertekend door het juiste licentieservercertificaat door het aanroepen `PolicyUpdateList.verifySignature()`.
1. Om te controleren of een ingang werd ingetrokken, ga beleidsidentiteitskaart `String` in `PolicyUpdateList.isRevoked()`. De lijst kan ook worden doorgegeven `HandlerConfiguration` en wordt gehandhaafd wanneer vergunningen worden afgegeven.

Als u aanvullende items wilt toevoegen aan een bestaande `PolicyUpdateList`, laadt u een bestaande lijst met beleidsupdates. Maak een nieuwe `PolicyUpdateListFactory` instantie. Vraag P `olicyUpdateListFactory.addEntries` om alle ingangen van de oude lijst aan de nieuwe lijst toe te voegen. Vraag `PolicyUpdateListFactory.addRevocationEntry` of `addUpdatedEntry` om het even welke nieuwe herroeping of update ingangen aan PolicyUpdateList toe te voegen.

Voor steekproefcode die aantonen hoe te om een lijst van de beleidsupdate tot stand te brengen, een bestaande lijst van beleidsupdates te laden, en te controleren of een beleid is ingetrokken, zie `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` in de folder van de &quot;steekproeven&quot;van de Lijn van het Bevel van de Toepassing van de Verwijzing Hulpmiddelen.
