---
description: 'null'
seo-description: 'null'
seo-title: Eigenschappen van licentieserver
title: Eigenschappen van licentieserver
uuid: 5e94ed1f-1dbf-4506-a097-183fcd5d25ef
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Eigenschappen van licentieserver{#license-server-properties-file}

De referenties van de licentieserver zijn ingesteld in het [!DNL flashaccess-refimpl.properties]-bestand. U kunt rechtstreeks naar dat bestand verwijzen voor meer informatie over specifieke waarden en voor gebruiksinformatie over elke eigenschap. Er wordt een volledig functioneel voorbeeld gegeven in de map [!DNL resources] van de referentie-implementatie ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`).

**Referenties**  - Het eigenschappenbestand bevat instellingen voor de locatie van de referenties die Adobe aan u geeft. U kunt deze geloofsbrieven in een [!DNL .pfx] dossier met een wachtwoord specificeren, of een alias en een wachtwoord voor een referentie verstrekken die op HSM wordt opgeslagen. U moet minstens de eigenschappen vormen die met de Credentials van het Vervoer en de Referentie van de Server van de Vergunning verwant zijn. Geef de locaties van de referentiebestanden op ten opzichte van de map die u opgeeft in de eigenschap `config.resourcesDirectory`.

**Flash Media Rights Management Server**  - Het  `flashaccess-refimpl.properties` bestand bevat ook diverse eigenschappen die verwant zijn aan het verpakken van inhoud. Deze eigenschappen worden slechts gebruikt voor de Flash Media Rights Management Server 1.x meta-gegevensomzetting. Nadat u de waarden in dit eigenschappenbestand hebt gewijzigd, worden de wijzigingen van kracht. Start vervolgens de licentieserver opnieuw.
