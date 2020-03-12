---
seo-title: Tenant-configuratiebestand
title: Tenant-configuratiebestand
uuid: 6e5c82c9-b8f5-4fca-8325-a884b2c779f7
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# Tenant-configuratiebestand {#tenant-configuration-file}

Het flashaccess-huurder.xml- configuratiedossier bevat montages die op een specifieke huurder van de vergunningsserver van toepassing zijn. Elke huurder heeft zijn eigen instantie van dit configuratiedossier dat in *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname *wordt gevestigd. Zie de[!DNL configs/flashaccessserver/tenants/sampletenant]folder voor een dossier van de voorbeeldhuurdersconfiguratie.

U kunt alle dossierwegen in het dossier van de huurdersconfiguratie als absolute wegen of wegen met betrekking tot de de configuratiemap van de huurder (*LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname *) specificeren.

Het configuratiebestand voor de huurder bevat:

* **Transport Credential** — Geeft een of meer transportreferenties (certificaat en persoonlijke sleutel) aan die door Adobe zijn uitgegeven. Kan worden opgegeven als een pad naar een .pfx-bestand en een wachtwoord, of als een alias voor een referentie die is opgeslagen op een HSM. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd. Zie &quot;Certificaatupdates[](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-cert-updates.md)verwerken&quot; in de SDK van Adobe Access *gebruiken voor het beveiligen van inhoud* voor meer informatie over wanneer extra referenties nodig zijn.
* **Referentie** licentieserver — Geeft een of meer referenties voor de licentieserver (certificaat en persoonlijke sleutel) op die door Adobe zijn uitgegeven. Kan worden opgegeven als een pad naar een .pfx-bestand en een wachtwoord, of als een alias voor een referentie die is opgeslagen op een HSM. Verscheidene dergelijke geloofsbrieven kunnen hier, of als dossierwegen, of belangrijkste aliassen, of allebei worden gespecificeerd. Zie Certificaatupdates verwerken in *De Adobe Access SDK gebruiken voor het beveiligen van inhoud *voor meer informatie over wanneer extra referenties nodig zijn.
* **Sleutelservercertificaten** — Optioneel. Geeft het licentieservercertificaat van de toetsserver op dat door Adobe is uitgegeven. Kan worden opgegeven als een pad naar een .cer-bestand of een alias naar een certificaat dat is opgeslagen op een HSM. Deze optie moet worden opgegeven om licenties te kunnen verlenen voor inhoud die is verpakt met een beleid waarvoor levering via externe sleutels voor iOS-apparaten is vereist.
* **Aangepaste autorisatoren** — Optioneel. Geeft aangepaste autorisatorklassen op die voor elke licentieaanvraag moeten worden aangeroepen. Als er meerdere autorisatoren zijn opgegeven, worden deze in de vermelde volgorde aangeroepen. Zie &quot;Extensies voor[aangepaste machtigingen](../../aaxs-protected-streaming/custom-authorization-extensions.md)&quot; voor meer informatie.
* **Lijst van goedgekeurde pakketten** — Optioneel. Geeft certificaten aan die entiteiten identificeren die geautoriseerd zijn om inhoud voor deze licentieserver te verpakken. Als er geen pakketcertificaten zijn opgegeven, geeft de server licenties voor inhoud uit die door een verpakker is verpakt.
* **Minimaal ondersteunde clientversie** (zie de SDK van Adobe Access *gebruiken voor het beschermen van inhoud*).
* **Gebruiksregels**

   * **Licentie in cache plaatsen** — optioneel. Hiermee geeft u op hoe lang de licentie op de client kan worden opgeslagen. Het in cache plaatsen van licenties is standaard uitgeschakeld. Om het in cache plaatsen van licenties voor een beperkte periode mogelijk te maken, stelt u de einddatum of het aantal seconden in waarvoor de licentie moet worden opgeslagen (te beginnen bij de afgifte van de vergunning). Als u het aantal seconden instelt op 0, wordt het in cache plaatsen van licenties uitgeschakeld.

      Alle licenties die door de Server voor Protected Streaming zijn uitgegeven, hebben een vervalperiode van 24 uur (86400 seconden). Deze waarde is daarom impliciet van toepassing als bovengrens aan wat einddatum of duur voor vergunning het in cache plaatsen eveneens wordt geplaatst, met een maximumwaarde van 86400 seconden, alhoewel het schema hogere grenzen afdwingt.

   * **Rechts** afspelen — Er moet ten minste één recht worden opgegeven. Als er meerdere rechten zijn opgegeven, gebruikt de client het eerste recht waarvoor het voldoet aan alle vereisten.

      * **Uitvoerbeveiliging** — Hiermee wordt bepaald of uitvoer naar externe renderingapparaten moet worden beveiligd.
      * **Beperkingen** voor AIR- en SWF-toepassingen — Optionele whitelist van SWF- en AIR-toepassingen die de inhoud kunnen afspelen (dus alleen de opgegeven toepassingen zijn toegestaan). SWF-toepassingen worden geïdentificeerd door een URL of door de samenvatting van het SWF-bestand en de maximale tijd die nodig is om de samenvatting te downloaden en te controleren. Zie de sectie SWF-hash Calculator voor informatie over het berekenen van de SWF-digest. AIR- en iOS-toepassingen worden aangeduid met een uitgevers-id en een optionele toepassings-id, een minimale versie en een maximale versie. Als er geen toepassingsbeperkingen zijn opgegeven, kan de inhoud door een SWF- of AIR-toepassing worden afgespeeld.
      * **DRM- en Runtime Module-beperkingen** — Geeft het minimale beveiligingsniveau op dat is vereist voor de DRM/Runtime-module. Bevat optioneel een zwarte lijst met versies die de inhoud niet mogen afspelen. Moduleversies worden geïdentificeerd door kenmerken zoals het besturingssysteem en/of een versienummer. De beperkingen van de Module DRM en de Beperkingen van de Runtime Module steunen nu de volgende extra attributen:

         * `oemVendor`
         * `model`
         * `screenType`
         De volgende kenmerken zijn nu optioneel:

         * `osVersion`
         * `version`
      * **Apparaatcapaciteitseisen** — Optioneel de hardwaremogelijkheden opgegeven die vereist zijn voor toegang tot inhoud.
      * **Eisen** voor Jailbreak-detectie — Optioneel wordt opgegeven dat afspelen niet is toegestaan voor apparaten waarop jailbreak wordt gedetecteerd.



Zie de commentaren in het de configuratiedossier van de voorbeeldhuurder voor meer details.
