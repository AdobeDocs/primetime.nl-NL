---
title: Tenant-configuratiebestand
description: Tenant-configuratiebestand
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Tenant-configuratiebestand {#tenant-configuration-file}

Het flashaccess-huurder.xml- configuratiedossier bevat montages die op een specifieke huurder van de vergunningsserver van toepassing zijn. Elke huurder heeft zijn eigen instantie van dit configuratiedossier dat in wordt gevestigd *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname*. Zie de [!DNL configs/flashaccessserver/tenants/sampletenant] directory voor een voorbeeld van een configuratiebestand van de huurder.

U kunt alle dossierwegen in het dossier van de huurdersconfiguratie als absolute wegen of wegen met betrekking tot de de configuratiemap van de huurder specificeren (*LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname*).

Het configuratiebestand voor de huurder bevat:

* **Vervoersreferentie** — Geeft een of meer transportreferenties (certificaat en persoonlijke sleutel) aan die door de Adobe worden uitgegeven. Kan worden opgegeven als een pad naar een .pfx-bestand en een wachtwoord, of als een alias voor een referentie die is opgeslagen op een HSM. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd. Zie &quot;[Certificaatupdates verwerken](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-cert-updates.md)&quot; in *De Adobe Access SDK gebruiken voor het beveiligen van inhoud* voor meer informatie over wanneer de extra geloofsbrieven worden vereist.
* **Credentieserverreferentie** — Geeft een of meer referenties voor licentieservers (certificaat en persoonlijke sleutel) op die door de Adobe worden uitgegeven. Kan worden opgegeven als een pad naar een .pfx-bestand en een wachtwoord, of als een alias voor een referentie die is opgeslagen op een HSM. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd. Zie Certificaatupdates verwerken in *Using de Adobe Access SDK voor het beschermen van inhoud *voor meer informatie over wanneer extra geloofsbrieven nodig zijn.
* **Belangrijke servercertificaten** — Optioneel. Specificeert het certificaat van de Server van de Vergunning van de Server van de Sleutel door Adobe wordt uitgegeven. Kan worden opgegeven als een pad naar een .cer-bestand of een alias naar een certificaat dat is opgeslagen op een HSM. Deze optie moet worden opgegeven om licenties te kunnen verlenen voor inhoud die is verpakt met een beleid waarvoor levering via externe sleutels voor iOS-apparaten is vereist.
* **Aangepaste autorisatoren** — Optioneel. Geeft aangepaste autorisatorklassen op die voor elke licentieaanvraag moeten worden aangeroepen. Als er meerdere autorisatoren zijn opgegeven, worden deze in de vermelde volgorde aangeroepen. Zie voor meer informatie &quot;[Aangepaste extensies voor machtigingen](../../aaxs-protected-streaming/custom-authorization-extensions.md)&quot;.
* **Lijst met geautoriseerde pakketten** — Optioneel. Geeft certificaten aan die entiteiten identificeren die geautoriseerd zijn om inhoud voor deze licentieserver te verpakken. Als er geen pakketcertificaten zijn opgegeven, geeft de server licenties voor inhoud uit die door een verpakker is verpakt.
* **Minimaal ondersteunde clientversie** (Zie *De Adobe Access SDK gebruiken voor het beveiligen van inhoud*).
* **Gebruiksregels**

   * **Licentie in cache plaatsen** — Optioneel. Hiermee geeft u op hoe lang de licentie op de client kan worden opgeslagen. Het in cache plaatsen van licenties is standaard uitgeschakeld. Om het in cache plaatsen van licenties voor een beperkte periode mogelijk te maken, stelt u de einddatum of het aantal seconden in waarvoor de licentie moet worden opgeslagen (te beginnen bij de afgifte van de vergunning). Als u het aantal seconden instelt op 0, wordt het in cache plaatsen van licenties uitgeschakeld.

     Alle licenties die door de Server voor Protected Streaming zijn uitgegeven, hebben een vervalperiode van 24 uur (86400 seconden). Deze waarde is daarom impliciet van toepassing als bovengrens aan wat einddatum of duur voor vergunning het in cache plaatsen eveneens wordt geplaatst, met een maximumwaarde van 86400 seconden, alhoewel het schema hogere grenzen afdwingt.

   * **Rechts afspelen** — Ten minste één recht moet worden gespecificeerd. Als er meerdere rechten zijn opgegeven, gebruikt de client het eerste recht waarvoor het voldoet aan alle vereisten.

      * **Uitvoerbeveiliging** — Bepaalt of uitvoer naar externe renderingapparaten moet worden beveiligd.
      * **Beperkingen voor AIR- en SWF-toepassingen** — Optionele lijst van gewenste personen van SWF- en AIR-toepassingen die de inhoud kunnen afspelen (d.w.z. alleen de opgegeven toepassingen zijn toegestaan). SWF-toepassingen worden aangegeven met een URL of met de samenvatting van de SWF en de maximale tijd die nodig is om het overzicht te downloaden en te controleren. Zie de sectie &quot;SWF Hash Calculator&quot; in de sectie &quot;SWF voor het berekenen van de digest. AIR- en iOS-toepassingen worden aangeduid met een uitgevers-id en een optionele toepassings-id, een minimale versie en een maximale versie. Als er geen toepassingsbeperkingen zijn opgegeven, kan de inhoud worden afgespeeld door een SWF- of AIR-toepassing.
      * **Beperkingen voor DRM en Runtime Module** — Geeft het minimale beveiligingsniveau op dat vereist is voor de DRM/Runtime-module. Bevat optioneel een lijst van gewezen personen met versies die de inhoud niet mogen afspelen. Moduleversies worden geïdentificeerd door kenmerken zoals het besturingssysteem en/of een versienummer. De beperkingen van de Module DRM en de Beperkingen van de Runtime Module steunen nu de volgende extra attributen:

         * `oemVendor`
         * `model`
         * `screenType`

        De volgende kenmerken zijn nu optioneel:

         * `osVersion`
         * `version`

      * **Vereisten voor apparaatcapaciteit** — Geeft optioneel de hardwaremogelijkheden aan die vereist zijn voor toegang tot inhoud.
      * **Eisen inzake detectie van spelregels** — Optioneel wordt opgegeven dat het afspelen niet is toegestaan voor apparaten waarop jailbreak wordt gedetecteerd.

Zie de commentaren in het de configuratiedossier van de voorbeeldhuurder voor meer details.
