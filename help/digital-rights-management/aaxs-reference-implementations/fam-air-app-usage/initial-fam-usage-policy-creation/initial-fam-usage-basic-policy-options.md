---
title: Basisbeleidsopties
description: Basisbeleidsopties
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Basisbeleidsopties {#basic-policy-options}

In de volgende tabel worden de basisbeleidsvoorkeuren beschreven:

| Voorkeur | Beschrijving |
|---|---|
| Beleidsduur | Specifies the validity period of content protected with this policy. |
|  | Beginnen bij | De certificaten mogen pas op deze datum/tijd worden gebruikt. |
|  | Eindigen bij | De certificaten kunnen na deze datum/tijd niet meer worden gebruikt. |
|  | Einde na | Hier geeft u op hoe lang een licentie geldig is (in minuten), te beginnen bij het verpakken. |
| Licentie in cache plaatsen | Geeft aan of licenties door de client in de cache mogen worden opgeslagen. |
|  |  | De certificaten kunnen na deze datum/tijd niet meer worden gebruikt. |
|  | Verwijderen na | Hier geeft u op hoe lang een licentie geldig is (in minuten), te beginnen bij het tijdstip waarop de licentie door de licentieserver wordt uitgegeven. |
|  | Cache oneindig | De licentie kan voor onbepaalde tijd in het cachegeheugen worden opgeslagen op de client. |
|  | Geen licentie in cache plaatsen | De licentie wordt mogelijk niet in de cache opgeslagen door de client. Elke keer dat de gebruiker de inhoud afspeelt, moet een nieuwe licentie van de server worden verkregen. |
| Verificatie |  |
|  | Anoniem | Er is geen verificatie vereist om de inhoud weer te geven. |
|  | Geverifieerd | Gebruikersnaam/wachtwoord is vereist. |
| Licentietekening inschakelen | Hiermee kan een licentie worden bijgewerkt met behulp van een bovenliggende hoofdlicentie voor het bijwerken van batches van licenties. Zodra de bladlicentie verloopt, kan de server de client een hoofdlicentie geven, waardoor alle inhoud die met dit beleid is beveiligd, wordt vernieuwd. |

