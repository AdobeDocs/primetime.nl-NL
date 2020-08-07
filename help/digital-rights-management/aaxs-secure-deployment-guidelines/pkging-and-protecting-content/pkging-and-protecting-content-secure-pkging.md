---
seo-title: Inhoud veilig verpakken
title: Inhoud veilig verpakken
uuid: a5e7cc17-353b-47d1-b89c-a2ba3c9faca1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Inhoud veilig verpakken {#securely-packaging-content}

Het configuratiedossier voor het Adobe Access Media Packager bevellijnhulpmiddel vereist een referentie PKCS12 die tijdens het verpakken wordt gebruikt.

In de hulpmiddelen van de Lijn van het Bevel van de Implementatie van de Verwijzing, wordt het wachtwoord voor het PKCS12 geloofsbrieven- dossier opgeslagen in het flashaccess.properties- dossier in duidelijke teksten. Wees daarom voorzichtig met het beveiligen van de computer die als host fungeert voor dit bestand en zorg ervoor dat dit bestand zich in een veilige omgeving bevindt. (Zie [Fysieke veiligheid en toegang](../../aaxs-secure-deployment-guidelines/physical-sec-and-access.md)).

Packager gebruikt ook de certificaten van het Vervoer van de Server van de Vergunning en van de Server van de Vergunning. Zowel de integriteit als de vertrouwelijkheid van deze informatie moeten worden beschermd. Alleen bevoegde entiteiten mogen de verpakker gebruiken. Als een van uw persoonlijke sleutels is aangetast, stelt u Adobe Systems Incorporated hiervan onmiddellijk op de hoogte, zodat het certificaat kan worden ingetrokken.

>[!NOTE]
>
>Met de API kunt u dezelfde sleutel gebruiken voor meerdere stukken inhoud. Om het hoogste niveau van veiligheid te verzekeren, adviseren wij deze eigenschap slechts voor multi-beetjetarief FMS inhoud wordt gebruikt. Het wordt afgeraden dezelfde sleutel te gebruiken voor meerdere bestanden die verschillende inhoud vertegenwoordigen.

De Adobe Access Packaging-API geeft onder bepaalde omstandigheden waarschuwingen weer. U moet deze waarschuwingen bekijken om te bepalen of uw bestanden zijn versleuteld. In de waarschuwingsberichten kan worden aangegeven dat het beleid is verlopen, dat een niet-herkende tag of track niet wordt gecodeerd, dat filmfragmenten niet worden gecodeerd (en dat verwijzingen in die fragmenten ongeldig worden) en dat metagegevens niet worden gecodeerd.

Als de inhoud gebruikend een beleid met onjuiste attributen verpakt is, zou het beleid moeten worden bijgewerkt, en het bijgewerkte beleid moet aan de Server van de Vergunning door een lijst van de beleidsupdate of een ander mechanisme ter beschikking worden gesteld om het bijgewerkte beleid aan de server te leveren. Sommige beleidskenmerken kunnen niet worden gewijzigd nadat het beleid is gemaakt. Als deze kenmerken onjuist zijn, trekt u de inhoud terug van de distributieplaatsen, trekt u het beleid in zodat geen toekomstige licenties kunnen worden verleend, en versleutelt u de inhoud opnieuw.

Wanneer het verpakken is voltooid, wordt de verpakkingssleutel niet expliciet vernietigd; het wordt echter opgeschoond. Daarom blijft de verpakkingssleutel gedurende een bepaalde periode in het geheugen aanwezig; u moet ervoor zorgen dat u geen bestanden, zoals kerndumpen, die deze informatie kunnen onthullen, toegankelijk maakt zonder toestemming.
