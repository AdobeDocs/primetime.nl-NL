---
title: Bestand met eigenschappen van Packager
description: Bestand met eigenschappen van Packager
copied-description: true
exl-id: 7d78576b-fd77-460d-92d9-c2e69e37006e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Bestand met eigenschappen van Packager {#packager-properties-file}

Gebruik de [!DNL flashaccess-refimpl-packager.properties] bestand om de component Watched Folder Packager van de referentie-implementatie te configureren. U moet ten minste de URL van de licentieserver, het licentieservercertificaat, de referentie van de verpakker en de beveiligingsopties voor toetsen instellen. Dit bestand bevat ook de locatie van elke gecontroleerde map (packager.watchfolder.source. `n`). Wijzigingen die worden aangebracht in de waarden in dit eigenschappenbestand, worden van kracht wanneer de controlemap weer wordt uitgevoerd (opnieuw opstarten van de server is niet vereist). Nochtans, als er een configuratiefout in de pakketsoftware is, zal de gelete op draad van het omslagpakket weggaan, en de server zal moeten opnieuw worden begonnen om de pakketdraad opnieuw te beginnen.
