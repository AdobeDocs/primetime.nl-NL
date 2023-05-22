---
title: Eigenschappen van licentieserver
description: Eigenschappen van licentieserver
copied-description: true
exl-id: 07cd9866-c29b-476e-a63f-9c5272ccd678
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Eigenschappen van licentieserver{#license-server-properties-file}

De referenties van de licentieserver zijn ingesteld in het dialoogvenster [!DNL flashaccess-refimpl.properties] bestand. U kunt rechtstreeks naar dat bestand verwijzen voor meer informatie over specifieke waarden en voor gebruiksinformatie over elke eigenschap. In de [!DNL resources] directory van de referentie-implementatie ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`).

**Credentials** - Het eigenschappenbestand bevat instellingen voor de locatie van de referenties die Adobe aan u geeft. U kunt deze gegevens opgeven in een [!DNL .pfx] bestand met een wachtwoord, of geef een alias en wachtwoord op voor een referentie die is opgeslagen op een HSM. U moet minstens de eigenschappen vormen die met de Credentials van het Vervoer en de Referentie van de Server van de Vergunning verwant zijn. Geef de locaties van de referentiebestanden op in verhouding tot de map die u in het dialoogvenster `config.resourcesDirectory` eigenschap.

**Flash Media Rights Management Server** - de `flashaccess-refimpl.properties` Het bestand bevat ook diverse eigenschappen die verwant zijn aan verpakkingsinhoud. Deze eigenschappen worden slechts gebruikt voor de Flash Media Rights Management Server 1.x meta-gegevensomzetting. Nadat u de waarden in dit eigenschappenbestand hebt gewijzigd, worden de wijzigingen van kracht. Start vervolgens de licentieserver opnieuw.
