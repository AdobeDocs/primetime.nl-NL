---
seo-title: Werken met DRM-beleidsupdatelijsten
title: Werken met DRM-beleidsupdatelijsten
uuid: 41f89671-81c6-4d3d-ac31-9c2a1980517a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# Lijst met updates voor DRM-beleid {#drm-policy-update-lists}

Als u de gebruiksregels in een DRM-beleid bijwerkt nadat u inhoud hebt verpakt, moet de licentieserver over de nieuwste versie beschikken voordat deze licenties kan uitgeven die een bijgewerkt DRM-beleid gebruiken. Één manier om dit te bereiken is door een DRM beleidsupdate lijst.

Een lijst met DRM-beleidsupdates wordt weergegeven door een bestand dat een lijst bevat met bijgewerkte of ingetrokken DRM-beleidsregels. Wanneer u een beleid DRM bijwerkt, moet u een nieuwe Lijst van de Update van het Beleid DRM produceren en periodiek de lijst aan alle vergunningsservers duwen.

## Werken met DRM-beleidsupdatelijsten {#working-with-drm-policy-update-lists}

Voor licentieservers die geen toegang hebben tot een database voor het opslaan van informatie over DRM-beleid, kunt u een lijst met DRM-beleidsupdates gebruiken om de licentieserver op de hoogte te stellen van elk bijgewerkt DRM-beleid. De lijsten van de Update van het Beleid DRM kunnen bijgewerkte versies van beleid DRM of een lijst van DRM beleids IDs omvatten die zijn ingetrokken. Als een lijst met beleidsupdates is opgenomen in `HandlerConfiguration`, dwingt de SDK deze lijst af wanneer een licentie wordt uitgegeven.

U kunt ook elk DRM-beleid intrekken als eigenaars of distributeurs van inhoud het afgeven van licenties onder een bepaald DRM-beleid willen beëindigen. Een lijst met DRM-beleidsupdates kan worden gebruikt om intrekking van DRM-beleid in de SDK af te dwingen. U kunt DRM-beleidsupdate-lijsten ook toepassen om een lijst met bijgewerkte DRM-beleidsregels op te geven aan de SDK.

>[!NOTE]
>
>Wanneer u een DRM-beleid intrekt, worden licenties die al zijn uitgegeven niet automatisch ingetrokken. Het voorkomt alleen dat er extra licenties worden uitgegeven in het kader van dat DRM-beleid.

## Beleidsupdatelijsten bijwerken{#update-policy-update-lists}

Wanneer u werkt met DRM-lijsten voor beleidsupdates, gebruikt u een `PolicyUpdateListFactory`-object. Als u een lijst van DRM beleidsupdate wilt tot stand brengen, moet u een bestaande DRM beleidsupdate lijst laden, en dan controleren of een beleid DRM door Java API is bijgewerkt of ingetrokken.

Om met de Lijsten van de Update van het Beleid te werken DRM:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden opgenomen wanneer u de ontwikkelomgeving instelt in een project.
1. Maak een `ServerCredentialFactory`-instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Maak een `PolicyUpdateListFactory`-instantie met de `ServerCredential` die u hebt gemaakt.
1. Geef de DRM-beleids-id op die u wilt intrekken.
1. Maak een `PolicyRevocationEntry`-object met de DRM-beleids-id `String` die u net hebt gemaakt, en voeg deze vervolgens toe aan de lijst met DRM-beleidsupdates door deze door te geven naar `PolicyUpdateListFactory.addRevocationEntry()`.
1. Genereer de nieuwe lijst met DRM-beleidsupdates door `PolicyUpdateListFactory.generatePolicyUpdateList()` aan te roepen.

   Op dezelfde manier kunt u beleid DRM aan de lijst bijwerken door `PolicyUpdateEntry` te gebruiken.
1. Als er al een lijst met DRM-beleidsupdates bestaat, kunt u deze serialiseren voor het laden door `PolicyUpdateList.getBytes()` aan te roepen.

   Om de lijst te laden, vraag `PolicyUpdateListFactory.loadPolicyUpdateList()` en ga het in de geserialiseerde lijst over.
1. Controleer of de handtekening geldig is en de lijst is ondertekend door het juiste licentieservercertificaat door `PolicyUpdateList.verifySignature()` aan te roepen.
1. Geef de DRM-beleids-id `String` door in `PolicyUpdateList.isRevoked()` om te controleren of een item is ingetrokken.

   U kunt de lijst ook doorgeven naar `HandlerConfiguration` waar deze wordt toegepast wanneer licenties worden uitgegeven.
Als u meer ingangen aan bestaande `PolicyUpdateList` wilt toevoegen, moet u een bestaande DRM lijst van beleidsupdate laden. Daarom moet u een nieuwe instantie DRM `PolicyUpdateListFactory` tot stand brengen. Roep `PolicyUpdateListFactory.addEntries` aan om alle ingangen van de oude lijst aan de nieuwe lijst toe te voegen. Roep `PolicyUpdateListFactory.addRevocationEntry` of `addUpdatedEntry` aan om het even welke nieuwe herroeping of update ingangen aan DRM PolicyUpdateList toe te voegen.

Zie `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` in de *Referentie-opdrachtregelprogramma&#39;s voor implementatie* [!DNL samples] voor voorbeeldcode die laat zien hoe u een lijst met DRM-beleidsupdates maakt.
