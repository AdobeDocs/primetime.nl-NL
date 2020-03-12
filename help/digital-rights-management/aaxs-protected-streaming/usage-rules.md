---
seo-title: Gebruiksregels
title: Gebruiksregels
uuid: 361d07b9-e4c8-47ab-8c45-a1de98c9fed7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gebruiksregels{#usage-rules}

Met de Adobe Access-server voor beveiligde streaming worden alle gebruiksregels op de server opgegeven via configuratiebestanden. Alle gebruiksregels die in de beveiligde inhoud zijn opgegeven, worden overschreven. Het wordt daarom aanbevolen een eenvoudig anonieme regel te gebruiken tijdens het verpakken van inhoud. De regels van het gebruik die configureerbaar zijn kunnen op een per-huurdersbasis worden geplaatst.

De Adobe Access-server voor beveiligde streaming ondersteunt de volgende gebruiksregels:

* Uitvoerbeveiliging
* Beperkingen voor Adobe® AIR®-, SWF-, iOS- en Android-toepassingen
* Beperkingen voor DRM en Runtime Module
* Handhaving voor Jailbreak-detectie (op Adobe Access-platforms die ondersteuning bieden voor jailbreak-detectie)
* Licentie in cache plaatsen is standaard uitgeschakeld. Licentie in cache plaatsen kan worden ingeschakeld door de einddatum van de caching op te geven of door een hoeveelheid tijd in cache te plaatsen (te beginnen bij de afgifte van de licentie).
* Meerdere afspeelrechten waarmee u verschillende combinaties van uitvoerbeveiliging, toepassingsbeperkingen en DRM/Runtime-beperkingen kunt opgeven. Het is bijvoorbeeld mogelijk om verschillende uitvoerbeveiligingsvereisten voor elk clientplatform op te geven met de DRM Module Restriction with Output Protection.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Voor ondersteuning van levering via externe sleutels naar iOS-apparaten moet de levering via externe sleutels zijn ingeschakeld voor het beleid dat tijdens het verpakken wordt gebruikt. Dit plaatsen kan niet door de huurdersconfiguratie op de server worden gewijzigd. ***Adobe Primetime is vereist voor het maken van iOS-toepassingen waarmee met Adobe Access beveiligde inhoud kan worden afgespeeld.***

