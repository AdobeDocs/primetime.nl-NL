---
description: Met de Adobe Primetime DRM-server voor beveiligde streaming kunt u alle gebruiksregels op de server opgeven met configuratiebestanden.
title: Gebruiksregels
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Gebruiksregels{#about-usage-rules}

Met de Adobe Primetime DRM-server voor beveiligde streaming kunt u alle gebruiksregels op de server opgeven met configuratiebestanden.

Alle gebruiksregels die in het DRM-beleid voor de beveiligde inhoud zijn opgegeven, worden overschreven. Daarom raadt de Adobe u aan een eenvoudig, anoniem DRM-beleid te gebruiken tijdens het verpakken van inhoud. Om het even welke gebruiksregels die u kunt vormen kunnen op een per-huurdersbasis worden gevormd.

De Primetime DRM-server voor beveiligde streaming ondersteunt de volgende gebruiksregels:

* Uitvoerbeveiliging
* Toepassingsbeperkingen voor Adobe® AIR®, SWF, iOS en Android
* Beperkingen voor DRM en Runtime Module
* Handhaving voor Jailbreak-detectie op Primetime DRM-platforms die ondersteuning bieden voor jailbreak-detectie
* Licentie in cache plaatsen is standaard uitgeschakeld. Licentie in cache plaatsen die u kunt inschakelen door de einddatum van de caching op te geven of door een hoeveelheid tijd in cache te plaatsen, wordt gestart wanneer de licentie wordt uitgegeven.
* Meerdere afspeelrechten waarmee u verschillende combinaties van uitvoerbeveiliging, toepassingsbeperkingen en DRM/Runtime-beperkingen kunt opgeven. U kunt bijvoorbeeld verschillende uitvoerbeveiligingsvereisten voor elk clientplatform opgeven met de DRM Module Restriction with Output Protection.

>[!NOTE]
>
>Als u levering via een externe toets aan iOS-apparaten wilt ondersteunen, moet voor het DRM-beleid dat wordt toegepast tijdens het verpakken de levering via een externe toets zijn ingeschakeld. Dit plaatsen kan niet door de huurdersconfiguratie op de server worden gewijzigd.
