---
description: Met de Adobe Primetime DRM-server voor beveiligde streaming kunt u alle gebruiksregels op de server opgeven met configuratiebestanden.
title: Gebruiksregels
exl-id: 55af3a18-8fdb-4285-bd9f-ca479475e34f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Gebruiksregels{#about-usage-rules}

Met de Adobe Primetime DRM-server voor beveiligde streaming kunt u alle gebruiksregels op de server opgeven met configuratiebestanden.

Alle gebruiksregels die in het DRM-beleid voor de beveiligde inhoud zijn opgegeven, worden overschreven. Daarom raadt Adobe u aan een eenvoudig, anoniem DRM-beleid te gebruiken tijdens het verpakken van inhoud. Om het even welke gebruiksregels die u kunt vormen kunnen op een per-huurdersbasis worden gevormd.

De Primetime DRM-server voor beveiligde streaming ondersteunt de volgende gebruiksregels:

* Uitvoerbeveiliging
* Beperkingen voor Adobe® AIR®-, SWF-, iOS- en Android-toepassingen
* Beperkingen voor DRM en Runtime Module
* Handhaving voor Jailbreak-detectie op Primetime DRM-platforms die ondersteuning bieden voor jailbreak-detectie
* Licentie in cache plaatsen is standaard uitgeschakeld. Het caching van de vergunning die u kunt toelaten door de caching einddatum of een hoeveelheid tijd caching wordt toegestaan; het begint bij de afgifte van de vergunning.
* Meerdere afspeelrechten waarmee u verschillende combinaties van uitvoerbeveiliging, toepassingsbeperkingen en DRM/Runtime-beperkingen kunt opgeven. U kunt bijvoorbeeld verschillende uitvoerbeveiligingsvereisten voor elk clientplatform opgeven met de DRM Module Restriction with Output Protection.

>[!NOTE]
>
>Als u levering via een externe toets aan iOS-apparaten wilt ondersteunen, moet voor het DRM-beleid dat wordt toegepast tijdens het verpakken de levering via een externe toets zijn ingeschakeld. Dit plaatsen kan niet door de huurdersconfiguratie op de server worden gewijzigd.
