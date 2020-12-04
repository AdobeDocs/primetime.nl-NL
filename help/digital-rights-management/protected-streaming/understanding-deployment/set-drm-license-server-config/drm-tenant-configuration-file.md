---
description: Het flashaccess-huurder.xml- configuratiedossier omvat montages die op een specifieke huurder van de vergunningsserver van toepassing zijn.
seo-description: Het flashaccess-huurder.xml- configuratiedossier omvat montages die op een specifieke huurder van de vergunningsserver van toepassing zijn.
seo-title: Tenant-configuratiebestand
title: Tenant-configuratiebestand
uuid: bc9ee4a1-63b6-4362-9929-3e9fe8251075
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# Tenant configuration file{#tenant-configuration-file}

Het flashaccess-huurder.xml- configuratiedossier omvat montages die op een specifieke huurder van de vergunningsserver van toepassing zijn.

Elke huurder steunt zijn eigen instantie van dit configuratiedossier dat in `<LicenseServer.ConfigRoot>/flashaccessserver/tenants/<tenantname>` wordt gevestigd. Zie `configs/flashaccessserver/tenants/sampletenant` folder voor een dossier van de voorbeeldhuurconfiguratie.

U kunt alle dossierwegen in het dossier van de huurdersconfiguratie als absolute wegen of als wegen specificeren die met betrekking tot de de configuratiemap van de huurder (`<LicenseServer.ConfigRoot>/flashaccessserver/tenants/<tenantname>`) zijn.

Het configuratiebestand voor de huurder bevat:

* *Vervoersreferentie* — Geeft een of meer transportreferenties (certificaat en persoonlijke sleutel) aan die door Adobe zijn uitgegeven. Kan worden opgegeven als een pad naar een [!DNL .pfx]-bestand en een wachtwoord, of als een alias voor een referentie die is opgeslagen op een HSM. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd.

   Zie *Certificaatupdates verwerken* in *De Adobe Primetime DRM SDK gebruiken voor het beveiligen van inhoud* voor meer informatie over wanneer extra referenties nodig zijn.

* *Referentie*  licentieserver - Geeft een of meer referenties voor licentieservers (certificaat en persoonlijke sleutel) op die door Adobe zijn uitgegeven. U kunt de referenties van de licentieserver opgeven als een pad naar een [!DNL .pfx]-bestand en een wachtwoord, of als een alias voor een referentie die is opgeslagen op een HSM. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd.

   Zie *Certificaatupdates verwerken* in *De Adobe Primetime DRM SDK gebruiken voor het beveiligen van inhoud* voor meer informatie over wanneer extra referenties nodig zijn.

* *Zeer belangrijke Certificaten*  van de Server - naar keuze specificeert het certificaat van de Server van de Vergunning van de Server van de Sleutel dat Adobe heeft uitgegeven. U kunt het certificaat van de Server van de Vergunning van de Server van de Sleutel als weg aan een [!DNL .cer] dossier of een alias aan een certificaat specificeren dat op HSM wordt opgeslagen. U moet deze optie opgeven om licenties te verlenen voor inhoud die is verpakt met een DRM-beleid waarvoor levering via externe sleutels voor iOS-apparaten is vereist.

* *Aangepaste autorisatoren*  - Optioneel worden aangepaste autorisatorklassen opgegeven die voor elke licentieaanvraag moeten worden aangeroepen. Als er meerdere autorisatoren zijn opgegeven, worden deze in de vermelde volgorde aangeroepen.
* *Lijst met geautoriseerde pakketten*  - Optioneel certificaten die entiteiten identificeren die geautoriseerd zijn om inhoud voor deze licentieserver te verpakken. Als er geen pakketcertificaten zijn opgegeven, geeft de server licenties voor inhoud uit die door een verpakker is verpakt. Als de server een vergunningsverzoek van een onbevoegd verpakker ontvangt, dan wordt het verzoek ontkend.
* *Minimaal ondersteunde* clientversieZie De Adobe Primetime DRM SDK gebruiken voor het beveiligen van inhoud.

* *Gebruiksregels*

   * *Licentie in cache plaatsen*  - Optioneel bepaalt u hoe lang u de licentie op de client kunt opslaan. Het in cache plaatsen van licenties is standaard uitgeschakeld. Als u het in cache plaatsen van licenties voor een beperkte periode wilt inschakelen, moet u de einddatum of het aantal seconden instellen waarvoor de licentie moet worden opgeslagen (te beginnen bij de afgifte van de licentie). Als u het aantal seconden instelt op 0, wordt het in cache plaatsen van licenties uitgeschakeld.

      >[!NOTE]
      >
      >Alle licenties die de Server for Protected Streaming heeft uitgegeven, hebben een vervalperiode van 24 uur (86400 seconden). Deze waarde is impliciet van toepassing als bovengrens aan wat einddatum of duur voor vergunning het in cache plaatsen eveneens wordt geplaatst, met een maximumwaarde van 86400 seconden, alhoewel het schema hogere grenzen afdwingt.

   * *Rechts*  afspelen - Er moet minimaal één recht worden opgegeven. Als u meerdere rechten opgeeft, gebruikt de client het eerste recht dat aan alle vereisten voldoet.

      * *Uitvoerbeveiliging* : bepaalt of uitvoer naar externe renderingapparaten moet worden beveiligd.
      * *Beperkingen*  voor AIR- en SWF-toepassingen: optionele lijst van gewenste personen van SWF- en AIR-toepassingen die de inhoud kunnen afspelen (bijvoorbeeld alleen de opgegeven toepassingen zijn toegestaan). SWF-toepassingen worden geïdentificeerd door een URL of door de samenvatting van het SWF-bestand en de maximale tijd die nodig is om de samenvatting te downloaden en te controleren.

         Zie *SWF-hash Calculator* voor informatie over het berekenen van de SWF-digest.

         Een uitgevers-id en een optionele toepassings-id, een minimale versie en een maximale versie identificeren AIR- en iOS-toepassingen. Als u geen toepassingsbeperkingen opgeeft, kan elke SWF- of AIR-toepassing de inhoud afspelen.

      * *Beperkingen*  voor DRM en Runtime Module - Geeft het minimale beveiligingsniveau op dat is vereist voor de DRM/Runtime-module. Bevat optioneel een lijst van afgewezen personen met versies die de inhoud niet mogen afspelen. Moduleversies worden aangeduid met kenmerken, zoals een besturingssysteem en/of een versienummer.

         De beperkingen van de Module DRM en de Beperkingen van de Runtime Module steunen nu de volgende extra attributen:

         * `oemVendor`
         * `model`
         * `screenType`

         De volgende kenmerken zijn nu optioneel:

         * `osVersion`
         * `version`
      * *Apparaatcapaciteitseisen*  — Optioneel de hardwaremogelijkheden opgegeven die vereist zijn voor toegang tot inhoud.
      * *Eisen*  voor Jailbreak-detectie - Optioneel wordt opgegeven dat afspelen niet is toegestaan voor apparaten waarop jailbreak wordt gedetecteerd.



Zie de commentaren in het de configuratiedossier van de voorbeeldhuurder voor meer details.
