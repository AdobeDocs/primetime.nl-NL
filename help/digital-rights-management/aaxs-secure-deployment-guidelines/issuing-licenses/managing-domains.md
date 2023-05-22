---
title: Domeinen beheren
description: Domeinen beheren
copied-description: true
exl-id: c9030373-fd54-4745-9f03-0218532b9d6d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Domeinen beheren{#managing-domains}

Om te voorkomen dat gebruikers een back-up kunnen maken van hun bestanden en deze kunnen herstellen in een poging om de deregistratie van domeinen te omzeilen, wordt aanbevolen een van de volgende methoden te gebruiken voor domeinbeheer:

* Beperk de hoeveelheid tijd de domeingeloofsbrieven geldig zijn. Clients moeten contact opnemen met de domeinserver om domeinreferenties opnieuw te verkrijgen wanneer ze verlopen. Op dat ogenblik, kan de Server van het Domein ervoor zorgen dat de machine nog wordt gemachtigd om een lid van het domein te zijn.
* Beweeg de muis over de domeinsleutels telkens wanneer een gebruiker de-registers opheft. De licentieserver mag alleen licenties uitgeven voor clients die over de nieuwste domeinsleutel beschikken. Hierbij wordt ervan uitgegaan dat de licentieserver kan samenwerken met de domeinserver om te weten welke sleutel het meest recente is. Wanneer u de domeinsleutels overschrijft, genereert u een nieuw sleutelpaar voor het domein. Wanneer u de toetsen voor een bepaald domein overschrijft, moet u de sleutelversie verhogen in `generateDomainCredential`. Ga voor meer informatie over het implementeren van een sleutelrollover naar *RefImplDomainReqHandler* in de referentieimplementatie.
* Als de domeinserver hetzelfde is als de licentieserver, kan de server de terugdraaiteller gebruiken om back-up en herstel te detecteren. Zie *Processing Adobe Access-aanvragen *in *De SDK van Adobe Access gebruiken voor het beveiligen van inhoud.*
