---
title: Gebruiksregels
description: Gebruiksregels
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Gebruiksregels{#usage-rules}

Met de Adobe Access Server for Protected Streaming worden alle gebruiksregels op de server opgegeven via configuratiebestanden. Alle gebruiksregels die in de beveiligde inhoud zijn opgegeven, worden overschreven. Het wordt daarom aanbevolen een eenvoudig anonieme regel te gebruiken tijdens het verpakken van inhoud. De regels van het gebruik die configureerbaar zijn kunnen op een per-huurdersbasis worden geplaatst.

De Adobe Access Server for Protected Streaming biedt ondersteuning voor de volgende gebruiksregels:

* Uitvoerbeveiliging
* Toepassingsbeperkingen voor Adobe® AIR®, SWF, iOS en Android
* Beperkingen voor DRM en Runtime Module
* De opsporingshandhaving van Jailbreak (op de platforms van de Toegang van de Adobe die jailbreak opsporing steunen)
* Licentie in cache plaatsen is standaard uitgeschakeld. Licentie in cache plaatsen kan worden ingeschakeld door de einddatum van de caching op te geven of door een hoeveelheid tijd in cache te plaatsen (te beginnen bij de afgifte van de licentie).
* Meerdere afspeelrechten waarmee u verschillende combinaties van uitvoerbeveiliging, toepassingsbeperkingen en DRM/Runtime-beperkingen kunt opgeven. Het is bijvoorbeeld mogelijk om verschillende uitvoerbeveiligingsvereisten voor elk clientplatform op te geven met de DRM Module Restriction with Output Protection.

>[!NOTE]
>
>Voor ondersteuning van levering via een externe toets aan iOS-apparaten moet voor het beleid dat tijdens het verpakken wordt gebruikt, levering via een externe toets zijn ingeschakeld. Dit plaatsen kan niet door de huurdersconfiguratie op de server worden gewijzigd. ***Adobe Primetime is vereist voor het maken van iOS-toepassingen waarmee met Adobe Access beveiligde inhoud kan worden afgespeeld.***
