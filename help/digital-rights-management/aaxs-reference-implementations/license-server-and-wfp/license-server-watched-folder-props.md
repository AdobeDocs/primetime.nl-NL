---
title: Eigenschappen van gecontroleerde mappen
description: Eigenschappen van gecontroleerde mappen
copied-description: true
exl-id: e86518d4-2a16-45c7-aa96-189f677c3ee6
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Eigenschappen van gecontroleerde mappen {#watched-folder-properties}

Elke gecontroleerde map bevat een bestand met de naam [!DNL properties/watchfolder.properties]. Dit bestand bevat de pakketopties voor inhoud die in deze map wordt geplaatst, inclusief wat er moet worden gecodeerd en welk beleid moet worden toegepast. Wijzigingen die u aanbrengt in de waarden in het eigenschappenbestand, worden van kracht wanneer de controlemap weer wordt uitgevoerd (u hoeft de server niet opnieuw te starten).

Als het eigenschappenbestand van Packager een configuratiefout bevat, stopt de thread van Packager. Start de server opnieuw om het gecontroleerde mappakketprogramma te hervatten. Als er een configuratiefout optreedt in een bestand met gecontroleerde mapeigenschappen, wordt de gecontroleerde map tijdelijk verwijderd uit de lijst met mappen die door de pakketsoftware wordt verwerkt. Als u de gecontroleerde map weer aan de lijst wilt toevoegen, start u de server opnieuw of wijzigt u het eigenschappenbestand van de pakketsoftware. Als een fout optreedt tijdens het verpakken van een bepaald bestand (bijvoorbeeld omdat het bestand beschadigd is), wordt het bestand overgeslagen en worden de resterende bestanden in de map verwerkt.
