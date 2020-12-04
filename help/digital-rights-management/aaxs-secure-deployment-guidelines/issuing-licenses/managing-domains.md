---
seo-title: Domeinen beheren
title: Domeinen beheren
uuid: aee02196-8704-46ee-add9-82b371722f0f
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Domeinen beheren{#managing-domains}

Om te voorkomen dat gebruikers een back-up kunnen maken van hun bestanden en deze kunnen herstellen in een poging om de deregistratie van domeinen te omzeilen, wordt aanbevolen een van de volgende methoden te gebruiken voor domeinbeheer:

* Beperk de hoeveelheid tijd de domeingeloofsbrieven geldig zijn. Clients moeten contact opnemen met de domeinserver om domeinreferenties opnieuw te verkrijgen wanneer ze verlopen. Op dat ogenblik, kan de Server van het Domein ervoor zorgen dat de machine nog wordt gemachtigd om een lid van het domein te zijn.
* Beweeg de muis over de domeinsleutels telkens wanneer een gebruiker de-registers opheft. De licentieserver mag alleen licenties uitgeven voor clients die over de nieuwste domeinsleutel beschikken. Hierbij wordt ervan uitgegaan dat de licentieserver kan samenwerken met de domeinserver om te weten welke sleutel het meest recente is. Wanneer u de domeinsleutels overschrijft, genereert u een nieuw sleutelpaar voor het domein. Wanneer het rollen over de sleutels voor een bepaald domein, ben zeker om de belangrijkste versie in `generateDomainCredential` te verhogen. Zie *RefImplDomainReqHandler* in de Reference Implementation voor meer informatie over het implementeren van een sleutelrollover.
* Als de domeinserver hetzelfde is als de licentieserver, kan de server de terugdraaiteller gebruiken om back-up en herstel te detecteren. Zie *Processing Adobe Access request *in *Gebruikend de Adobe Access SDK voor het beschermen van inhoud.*

