---
description: Het flashaccess-huurder.xml- configuratiedossier omvat montages die op een specifieke huurder van de vergunningsserver van toepassing zijn.
title: Tenant-configuratiebestand
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---

# Tenant-configuratiebestand{#tenant-configuration-file}

Het flashaccess-huurder.xml- configuratiedossier omvat montages die op een specifieke huurder van de vergunningsserver van toepassing zijn.

Elke huurder steunt zijn eigen geval van dit configuratiedossier dat in wordt gevestigd `<LicenseServer.ConfigRoot>/flashaccessserver/tenants/<tenantname>`. Zie de `configs/flashaccessserver/tenants/sampletenant` directory voor een voorbeeld van een configuratiebestand van de huurder.

U kunt alle dossierwegen in het dossier van de huurdersconfiguratie als absolute wegen of als wegen specificeren die met betrekking tot de de configuratiemap van de huurder (`<LicenseServer.ConfigRoot>/flashaccessserver/tenants/<tenantname>`).

Het configuratiebestand voor de huurder bevat:

* *Vervoersreferentie* — Geeft een of meer transportreferenties (certificaat en persoonlijke sleutel) aan die door de Adobe worden uitgegeven. Kan worden opgegeven als een pad naar een [!DNL .pfx] en een wachtwoord, of een alias voor een referentie die op HSM wordt opgeslagen. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd.

  Zie *Certificaatupdates verwerken* in *De Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud* voor meer informatie over wanneer de extra geloofsbrieven worden vereist.

* *Credentieserverreferentie* — Geeft een of meer referenties voor licentieservers (certificaat en persoonlijke sleutel) op die door de Adobe zijn uitgegeven. U kunt de referenties van de licentieserver opgeven als pad naar een [!DNL .pfx] en een wachtwoord, of een alias voor een referentie die op HSM wordt opgeslagen. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd.

  Zie *Certificaatupdates verwerken* in *De Adobe Primetime DRM SDK gebruiken voor het beschermen van inhoud* voor meer informatie over wanneer de extra geloofsbrieven worden vereist.

* *Belangrijke servercertificaten* — Optioneel wordt het licentieservercertificaat van de sleutelserver opgegeven dat de Adobe heeft uitgegeven. U kunt het certificaat van de Server van de Vergunning van de Sleutelserver als weg aan een server specificeren [!DNL .cer] bestand of een alias voor een certificaat dat is opgeslagen op een HSM. U moet deze optie opgeven om licenties te verlenen voor inhoud die is verpakt met een DRM-beleid waarvoor levering via externe sleutels voor iOS-apparaten is vereist.

* *Aangepaste autorisatoren* — Optioneel worden aangepaste autorisatorklassen opgegeven die voor elke licentieaanvraag moeten worden aangeroepen. Als er meerdere autorisatoren zijn opgegeven, worden deze in de vermelde volgorde aangeroepen.
* *Lijst met geautoriseerde pakketten* — Optioneel worden certificaten opgegeven ter identificatie van entiteiten die gemachtigd zijn inhoud voor deze licentieserver te verpakken. Als er geen pakketcertificaten zijn opgegeven, geeft de server licenties voor inhoud uit die door een verpakker is verpakt. Als de server een vergunningsverzoek van een onbevoegd verpakker ontvangt, dan wordt het verzoek ontkend.
* *Minimaal ondersteunde clientversie* Zie De Adobe Primetime DRM SDK gebruiken voor het beveiligen van inhoud.

* *Gebruiksregels*

   * *Licentie in cache plaatsen* — Optioneel geeft u aan hoe lang u de licentie op de client kunt opslaan. Het in cache plaatsen van licenties is standaard uitgeschakeld. Als u het in cache plaatsen van licenties voor een beperkte periode wilt inschakelen, moet u de einddatum of het aantal seconden instellen waarvoor de licentie moet worden opgeslagen (te beginnen bij de afgifte van de licentie). Als u het aantal seconden instelt op 0, wordt het in cache plaatsen van licenties uitgeschakeld.

     >[!NOTE]
     >
     >Alle licenties die de Server for Protected Streaming heeft uitgegeven, hebben een vervalperiode van 24 uur (86400 seconden). Deze waarde is impliciet van toepassing als bovengrens aan wat einddatum of duur voor vergunning het in cache plaatsen eveneens wordt geplaatst, met een maximumwaarde van 86400 seconden, alhoewel het schema hogere grenzen afdwingt.

   * *Rechts afspelen* — Er moet ten minste één recht worden vermeld. Als u meerdere rechten opgeeft, gebruikt de client het eerste recht dat aan alle vereisten voldoet.

      * *Uitvoerbeveiliging* — Bepaalt of uitvoer naar externe renderingapparaten moet worden beveiligd.
      * *Beperkingen voor AIR- en SWF-toepassingen* — Optionele lijst van gewenste personen van SWF- en AIR-toepassingen die de inhoud kunnen afspelen (bijvoorbeeld alleen de opgegeven toepassingen zijn toegestaan). SWF-toepassingen worden aangegeven met een URL of met de samenvatting van de SWF en de maximale tijd die nodig is om het overzicht te downloaden en te controleren.

        Zie *SWF Hash-calculator* voor informatie over hoe u de SWF-samenvatting kunt berekenen.

        Een uitgevers-id en een optionele toepassings-id, een minimale versie en een maximale versie identificeren AIR- en iOS-toepassingen. Als u geen toepassingsbeperkingen opgeeft, kan elke SWF- of AIR-toepassing de inhoud afspelen.

      * *Beperkingen voor DRM en Runtime Module* — Geeft het minimale beveiligingsniveau op dat vereist is voor de DRM/Runtime-module. Bevat optioneel een lijst van gewezen personen met versies die de inhoud niet mogen afspelen. Moduleversies worden aangeduid met kenmerken, zoals een besturingssysteem en/of een versienummer.

        De beperkingen van de Module DRM en de Beperkingen van de Runtime Module steunen nu de volgende extra attributen:

         * `oemVendor`
         * `model`
         * `screenType`

        De volgende kenmerken zijn nu optioneel:

         * `osVersion`
         * `version`

      * *Vereisten voor apparaatcapaciteit* — Geeft optioneel de hardwaremogelijkheden aan die vereist zijn voor toegang tot inhoud.
      * *Eisen inzake detectie van spelregels* — Optioneel wordt opgegeven dat het afspelen niet is toegestaan voor apparaten waarop jailbreak wordt gedetecteerd.

Zie de commentaren in het de configuratiedossier van de voorbeeldhuurder voor meer details.
