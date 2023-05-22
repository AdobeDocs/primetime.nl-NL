---
title: Prestaties afstemmen
description: Prestaties afstemmen
copied-description: true
exl-id: 1b54b7c2-da32-47db-b57f-b2afbaf386c4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Prestaties afstemmen{#performance-tuning}

Gebruik de volgende tips om de prestaties te verbeteren:

* Het gebruiken van een netwerk HSM kan beduidend langzamer zijn dan het gebruiken van direct-verbonden HSM.
* Voor betere prestaties, kunt u naar keuze inheemse steun voor cryptografische verrichtingen toelaten door de platform-specifieke bibliotheken op te stellen die in [!DNL thirdparty/cryptoj] map van de SDK. Als u native ondersteuning wilt inschakelen, voegt u de bibliotheek voor uw platform (jsafe.dll voor Windows of libjsafe.so voor Linux) toe aan het pad.

   >[!NOTE]
   >
   >Als u meerdere webtoepassingen uitvoert in hetzelfde Tomcat-exemplaar en als u `jsafe.dll` alleen de eerste webtoepassing die het pad laadt, kan het pad `jsafe.dll` bibliotheek. Daarom krijgt alleen de eerste webtoepassing het voordeel van de native ondersteuning. In dergelijke gevallen, om de prestaties van alle Webtoepassingen te verbeteren, plaats `cryptoj.jar`buiten het WAR-bestand. In het dialoogvenster `<tomcat_installation_folder>/lib` directory.

* Een 64-bits besturingssysteem, zoals de 64-bits versie van Red Hat® of Windows, biedt veel betere prestaties dan een 32-bits besturingssysteem.

## Willekeurige getallen genereren (Linux) {#section_3E2E936A538F40B7BF8892C65E117907}

Onder bepaalde omstandigheden kunnen Linux-omgevingen pauzeren bij het uitvoeren van DRM-gerelateerde bewerkingen met betrekking tot Primetime waarvoor willekeurige getallen moeten worden gegenereerd, zoals:

* Opstarten van de Adobe Primetime DRM-licentieserver
* Beleid genereren met behulp van [!DNL AdobePolicyManager] nut
* Door DRM beveiligde inhoud verpakken met Adobe Media Server of Primetime OfflinePackager

Vertragingen tijdens deze bewerkingen zijn vaak het resultaat van een lage entropiepool op uw Linux-server.

Op Linux worden willekeurige getallen gegenereerd uit de entropiepool van de serveromgeving. De entropiepool wordt normaal onderhouden door hardwareonderbrekingen door de Linux-kernel te ontvangen. Als een server geïsoleerd is en geen regelmatige input van middelen HW (zoals een muis of een toetsenbord) ontvangt, kan het wachten om de entropiepool te vullen worden uitgebreid. In dit scenario, verrichtingen die op gegevens van wachten [!DNL /dev/random] kan pauzeren.

U kunt hardware willekeurige nummergenerators op de servers van Linux gebruiken om ervoor te zorgen dat voldoende entropie wordt geproduceerd. Nochtans, als hardware willekeurige aantalgenerators niet beschikbaar in een bepaald plaatsingsscenario zijn, kunt u software gebaseerde oplossingen gebruiken om de entropiepool te verhogen verfrist tarief. Eén van deze softwareoplossingen op Linux is [!DNL haveged] (HArdware Volatile Entropy Gathering and Expansion daemon).

## Beschikbare Entropie bepalen {#section_686B311FE6144566B6939E9F20915ADC}

Om het aantal beetjes te verifiëren beschikbaar in de de entropiepool van een bepaalde server tijdens een onverwachte vertraging, voer het volgende bevel uit:

```
cat /proc/sys/kernel/random/entropy_avail 
```

Een gezond Linux-systeem met veel entropie is beschikbaar en retourneert bijna de volledige 4.096 bits entropie. Als de geretourneerde waarde lager is dan 200, wordt het systeem op entropie zeer laag uitgevoerd.
