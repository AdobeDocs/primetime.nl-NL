---
seo-title: Werken met DRM-beleidsupdatelijsten
title: Werken met DRM-beleidsupdatelijsten
uuid: 41f89671-81c6-4d3d-ac31-9c2a1980517a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Update-lijsten voor DRM-beleid {#drm-policy-update-lists}

Als u de gebruiksregels in een DRM-beleid bijwerkt nadat u inhoud hebt verpakt, moet de licentieserver over de nieuwste versie beschikken voordat deze licenties kan uitgeven die een bijgewerkt DRM-beleid gebruiken. Één manier om dit te bereiken is door een DRM beleidsupdate lijst.

Een lijst met DRM-beleidsupdates wordt weergegeven door een bestand dat een lijst bevat met bijgewerkte of ingetrokken DRM-beleidsregels. Wanneer u een beleid DRM bijwerkt, moet u een nieuwe Lijst van de Update van het Beleid DRM produceren en periodiek de lijst aan alle vergunningsservers duwen.

## Werken met DRM-beleidsupdatelijsten {#working-with-drm-policy-update-lists}

Voor licentieservers die geen toegang hebben tot een database voor het opslaan van informatie over DRM-beleid, kunt u een lijst met DRM-beleidsupdates gebruiken om de licentieserver op de hoogte te stellen van elk bijgewerkt DRM-beleid. De lijsten van de Update van het Beleid DRM kunnen bijgewerkte versies van beleid DRM of een lijst van DRM beleids IDs omvatten die zijn ingetrokken. Als een lijst met beleidsupdates is opgenomen in `HandlerConfiguration`, dwingt de SDK deze lijst af wanneer deze een licentie uitgeeft.

U kunt ook elk DRM-beleid intrekken als eigenaars of distributeurs van inhoud het afgeven van licenties onder een bepaald DRM-beleid willen beëindigen. Een lijst met DRM-beleidsupdates kan worden gebruikt om intrekking van DRM-beleid in de SDK af te dwingen. U kunt DRM-beleidsupdate-lijsten ook toepassen om een lijst met bijgewerkte DRM-beleidsregels op te geven aan de SDK.

>[!NOTE]
>
>Wanneer u een DRM-beleid intrekt, worden licenties die al zijn uitgegeven niet automatisch ingetrokken. Het voorkomt alleen dat er extra licenties worden uitgegeven in het kader van dat DRM-beleid.

## Lijst met beleidsupdates bijwerken{#update-policy-update-lists}

Wanneer u werkt met DRM-beleidsupdate, gebruikt u een `PolicyUpdateListFactory` object. Als u een lijst van DRM beleidsupdate wilt tot stand brengen, moet u een bestaande DRM beleidsupdate lijst laden, en dan controleren of een beleid DRM door Java API is bijgewerkt of ingetrokken.

Om met de Lijsten van de Update van het Beleid te werken DRM:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden opgenomen wanneer u de ontwikkelomgeving instelt in een project.
1. Maak een `ServerCredentialFactory` instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Maak een `PolicyUpdateListFactory` instantie met de `ServerCredential` instantie die u hebt gemaakt.
1. Geef de DRM-beleids-id op die u wilt intrekken.
1. Maak een `PolicyRevocationEntry` object met de DRM-beleids-id `String` die u net hebt gemaakt en voeg het object vervolgens toe aan de lijst met beleidsupdates voor DRM door het door te geven naar `PolicyUpdateListFactory.addRevocationEntry()`.
1. Genereer de nieuwe DRM lijst van de beleidsupdate door te roepen `PolicyUpdateListFactory.generatePolicyUpdateList()`.

   Op dezelfde manier kunt u beleid DRM aan de lijst bijwerken door te gebruiken `PolicyUpdateEntry`.
1. Als er al een lijst met DRM-beleidsupdates bestaat, kunt u deze serialiseren voor het laden door een aanroep te doen `PolicyUpdateList.getBytes()`.

   Om de lijst te laden, roep `PolicyUpdateListFactory.loadPolicyUpdateList()` en ga het in de geserialiseerde lijst over.
1. Controleer of de handtekening geldig is en of de lijst is ondertekend door het juiste licentieservercertificaat door het aanroepen `PolicyUpdateList.verifySignature()`.
1. Geef de DRM-beleids-id door `String` in `PolicyUpdateList.isRevoked()` om te controleren of een item is ingetrokken.

   U kunt de lijst ook doorgeven naar `HandlerConfiguration` waar deze wordt toegepast wanneer licenties worden uitgegeven.
Als u meer ingangen aan bestaand wilt toevoegen `PolicyUpdateList`, moet u een bestaande DRM lijst van de beleidsupdate laden. Daarom moet u een nieuwe DRM- `PolicyUpdateListFactory` instantie maken. Vraag `PolicyUpdateListFactory.addEntries` om alle ingangen van de oude lijst aan de nieuwe lijst toe te voegen. Vraag `PolicyUpdateListFactory.addRevocationEntry` of `addUpdatedEntry` om het even welke nieuwe herroeping of update ingangen aan DRM PolicyUpdateList toe te voegen.

Voor steekproefcode die aantoont hoe te om een DRM lijst van beleidsupdate tot stand te brengen, zie `com.adobe.flashaccess.samples.policyupdatelist` in de `.CreatePolicyUpdateList` folder van de Hulpmiddelen ** [!DNL samples] van de Lijn van de Lijn van het Bevel van de Implementatie van de Verwijzing.
