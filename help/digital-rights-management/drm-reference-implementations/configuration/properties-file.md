---
description: 'null'
seo-description: 'null'
seo-title: Eigenschappen van licentieserver
title: Eigenschappen van licentieserver
uuid: 5e94ed1f-1dbf-4506-a097-183fcd5d25ef
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Eigenschappen van licentieserver{#license-server-properties-file}

De licentieserver verwijst naar eigenschappen die in het [!DNL flashaccess-refimpl.properties] bestand zijn ingesteld. U kunt rechtstreeks naar dat bestand verwijzen voor meer informatie over specifieke waarden en voor gebruiksinformatie over elke eigenschap. In de [!DNL resources] directory van de referentie-implementatie ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`) wordt een volledig functioneel voorbeeld gegeven.

**Referenties** - Het eigenschappenbestand bevat instellingen voor de locatie van de referenties die Adobe aan u geeft. U kunt deze gegevens opgeven in een [!DNL .pfx] bestand met een wachtwoord of een alias en wachtwoord opgeven voor een referentie die is opgeslagen op een HSM. U moet minstens de eigenschappen vormen die met de Credentials van het Vervoer en de Referentie van de Server van de Vergunning verwant zijn. Geef de locaties van de referentiebestanden op ten opzichte van de map die u in de `config.resourcesDirectory` eigenschap opgeeft.

**Flash Media Rights Management Server** - Het `flashaccess-refimpl.properties` bestand bevat ook verschillende eigenschappen die verwant zijn aan het verpakken van inhoud. Deze eigenschappen worden alleen gebruikt voor de metagegevensconversie van Flash Media Rights Management Server 1.x. Nadat u de waarden in dit eigenschappenbestand hebt gewijzigd, worden de wijzigingen van kracht. Start vervolgens de licentieserver opnieuw.
