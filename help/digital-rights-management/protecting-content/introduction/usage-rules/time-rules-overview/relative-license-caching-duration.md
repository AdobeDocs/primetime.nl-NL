---
seo-title: Duur van licentiecache
title: Duur van licentiecache
uuid: d448aa43-8cba-4b1d-8609-0dba4bb67042
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Duur van licentiecache{#license-caching-duration}

De duur van het in cache plaatsen van licenties bepaalt hoe lang een licentie op schijf in de lokale licentieserve van de client in cache kan worden geplaatst zonder dat de licentie opnieuw moet worden opgehaald van de licentieserver. U kunt ook een absolute datum en tijd opgeven waarna een licentie niet langer in de cache kan worden opgeslagen.

Nadat de vervaldatum van de cache is verstreken, is de licentie niet meer geldig en moet de client een nieuwe licentie aanvragen bij de licentieserver.

Voorbeeld van gebruik: Gebruik de duur van het in cache plaatsen van licenties om een vaste tijdsduur op te geven die geldig is voor een bepaalde licentie, zoals in een gebruiksgeval voor verhuur. U kunt een verhuur van 30 dagen opgeven (met licentiecache) om de totale licentieduur aan te geven waarbinnen de inhoud moet worden geconsumeerd.
