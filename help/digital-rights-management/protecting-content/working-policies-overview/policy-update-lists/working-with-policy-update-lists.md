---
title: Werken met DRM-beleidsupdatelijsten
description: Werken met DRM-beleidsupdatelijsten
copied-description: true
exl-id: 140f1fff-2078-427b-ade2-8ec18a14216f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Update-lijsten voor DRM-beleid {#drm-policy-update-lists}

Als u de gebruiksregels in een DRM-beleid bijwerkt nadat u inhoud hebt verpakt, moet de licentieserver over de nieuwste versie beschikken voordat deze licenties kan uitgeven die een bijgewerkt DRM-beleid gebruiken. Één manier om dit te bereiken is door een DRM beleidsupdate lijst.

Een lijst met DRM-beleidsupdates wordt weergegeven door een bestand dat een lijst bevat met bijgewerkte of ingetrokken DRM-beleidsregels. Wanneer u een beleid DRM bijwerkt, moet u een nieuwe Lijst van de Update van het Beleid DRM produceren en periodiek de lijst aan alle vergunningsservers duwen.

## Werken met DRM-beleidsupdatelijsten {#working-with-drm-policy-update-lists}

Voor licentieservers die geen toegang hebben tot een database voor het opslaan van informatie over DRM-beleid, kunt u een lijst met DRM-beleidsupdates gebruiken om de licentieserver op de hoogte te stellen van elk bijgewerkt DRM-beleid. De lijsten van de Update van het Beleid DRM kunnen bijgewerkte versies van beleid DRM of een lijst van DRM beleids IDs omvatten die zijn ingetrokken. Als een lijst met beleidsupdates is opgenomen in `HandlerConfiguration`, dwingt de SDK deze lijst af wanneer een licentie wordt uitgegeven.

U kunt ook elk DRM-beleid intrekken als eigenaars of distributeurs van inhoud het afgeven van licenties onder een bepaald DRM-beleid willen beëindigen. Een lijst met DRM-beleidsupdates kan worden gebruikt om intrekking van DRM-beleid in de SDK af te dwingen. U kunt DRM-beleidsupdate-lijsten ook toepassen om een lijst met bijgewerkte DRM-beleidsregels op te geven aan de SDK.

>[!NOTE]
>
>Wanneer u een DRM-beleid intrekt, worden licenties die al zijn uitgegeven niet automatisch ingetrokken. Het voorkomt alleen dat er extra licenties worden uitgegeven in het kader van dat DRM-beleid.

## Lijst met beleidsupdates bijwerken{#update-policy-update-lists}

Het werken met DRM de lijsten van beleidsupdates impliceert het gebruik van een `PolicyUpdateListFactory` object. Als u een lijst van DRM beleidsupdate wilt tot stand brengen, moet u een bestaande DRM beleidsupdate lijst laden, en dan controleren of een beleid DRM door Java API is bijgewerkt of ingetrokken.

Om met de Lijsten van de Update van het Beleid te werken DRM:

1. Stel uw ontwikkelomgeving in en neem alle JAR-bestanden op die worden opgenomen wanneer u de ontwikkelomgeving instelt in een project.
1. Een `ServerCredentialFactory` -instantie om de referenties te laden die nodig zijn voor ondertekening.
1. Een `PolicyUpdateListFactory` instantie door de `ServerCredential` die u hebt gemaakt.
1. Geef de DRM-beleids-id op die u wilt intrekken.
1. Een `PolicyRevocationEntry` object met de DRM-beleids-id `String` die u net creeerde, en dan het toevoegen aan de DRM lijst van de beleidsupdate door het over te gaan in `PolicyUpdateListFactory.addRevocationEntry()`.
1. Genereer de nieuwe DRM-beleidsupdate door `PolicyUpdateListFactory.generatePolicyUpdateList()`.

   Op dezelfde manier kunt u beleid DRM aan de lijst bijwerken door te gebruiken `PolicyUpdateEntry`.
1. Als er al een lijst met DRM-beleidsupdates bestaat, kunt u deze voor het laden serialiseren door `PolicyUpdateList.getBytes()`.

   Om de lijst te laden, roep `PolicyUpdateListFactory.loadPolicyUpdateList()` en geef het in de geserialiseerde lijst door.
1. Controleer of de handtekening geldig is en de lijst is ondertekend door het juiste licentieservercertificaat door aan te roepen `PolicyUpdateList.verifySignature()`.
1. De DRM-beleids-id doorgeven `String` in `PolicyUpdateList.isRevoked()` om te controleren of een vermelding is ingetrokken.

   U kunt de lijst ook doorgeven aan `HandlerConfiguration` wanneer zij vervolgens wordt toegepast wanneer vergunningen worden afgegeven.
Als u meer items wilt toevoegen aan een bestaande `PolicyUpdateList`, moet u een bestaande DRM-beleidsupdate lijst laden. Daarom moet u een nieuw DRM creëren `PolicyUpdateListFactory` -instantie. Bellen `PolicyUpdateListFactory.addEntries` om alle vermeldingen uit de oude lijst toe te voegen aan de nieuwe lijst. Bellen `PolicyUpdateListFactory.addRevocationEntry` of `addUpdatedEntry` om nieuwe intrekkingsitems of bijgewerkte items toe te voegen aan de DRM PolicyUpdateList.

Voor steekproefcode die aantoont hoe te om een DRM lijst van beleidsupdate tot stand te brengen, zie `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` in de *Opdrachtregelprogramma voor naslagimplementatie* [!DNL samples] directory.
