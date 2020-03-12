---
seo-title: Bestand met eigenschappen van Packager
title: Bestand met eigenschappen van Packager
uuid: 156624ec-66f0-4718-8a66-ed04a47f234d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Bestand met eigenschappen van Packager {#packager-properties-file}

Gebruik het [!DNL flashaccess-refimpl-packager.properties] bestand om de component Watched Folder Packager van de referentie-implementatie te configureren. U moet ten minste de URL van de licentieserver, het licentieservercertificaat, de referentie van de verpakker en de beveiligingsopties voor toetsen instellen. Dit bestand bevat ook de locatie van elke gecontroleerde map (packager.watchfolder.source. `n`). Wijzigingen die worden aangebracht in de waarden in dit eigenschappenbestand, worden van kracht wanneer de controlemap weer wordt uitgevoerd (opnieuw opstarten van de server is niet vereist). Nochtans, als er een configuratiefout in de pakketsoftware is, zal de gelete op draad van het omslagpakket weggaan, en de server zal moeten opnieuw worden begonnen om de pakketdraad opnieuw te beginnen.
