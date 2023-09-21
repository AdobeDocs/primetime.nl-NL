---
title: De DRM-server uitvoeren voor beveiligde streaming
description: De DRM-server uitvoeren voor beveiligde streaming
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---

# De DRM-server uitvoeren voor beveiligde streaming {#running-the-drm-server-for-protected-streaming}

Voordat u de Adobe Primetime DRM-server kunt starten voor beveiligde streaming, is het raadzaam de geldigheid van de instellingen in de configuratiebestanden te controleren.

U kunt de geldigheid van de montages verifiëren door de nut te gebruiken die met de vergunningsserver zijn verstrekt. (Zie *Configuratievalidator* in deze handleiding.

Als u Tomcat en de licentieserver wilt starten, moet u [!DNL catalina.bat start] of [!DNL catalina.sh start] van Tomcat [!DNL bin] directory.

Nadat de server is begonnen, moet u verifiëren dat het correct is gevormd door te openen `https://<lic<span></span>ense-server-host:port>/flashaccessserver/<tenant-name>/flashaccess/license/v1` in een browservenster. Als de huurdersconfiguratie met succes is geladen, verschijnt een bevestigingsbericht.

## Logbestanden {#log-files}

De logbestanden die worden gegenereerd door de Adobe Primetime DRM-server voor beveiligde streaming-toepassing bevinden zich in de map die is opgegeven door LicenseServer.LogRoot.

>[!NOTE]
>
>Als de huidige logbestanden worden verwijderd of verplaatst terwijl de server wordt uitgevoerd, wordt het logbestand mogelijk niet opnieuw gemaakt. Daarom kunnen sommige logboekinformatie worden geschrapt.

### Logboekmapstructuur {#section_F490A483D60145ADBC21038914C39203}

Logmappen zijn gestructureerd voor gebruiksgemak. De logmap heeft de volgende structuur:

```
<i class="+ topic ph hi-d="" i "="">
 LicenseServer.LogRoot/ 
 flashaccess-global.log 
     flashaccessserver/ 
         flashaccess-partition.log 
         tenants/ 
             
 <i class="+ topic ph hi-d="" i "="">
  tenantname/ 
                  flashaccess-tenant.log
 </i class="+ topic>
</i class="+ topic>
```

### Globaal logbestand {#section_1CFA90748142439C9F3BE380969539DA}

Het algemene logbestand, [!DNL flashaccess-global.log], bevindt zich in *LicenseServer.LogRoot*. Het logboek kan logboekberichten omvatten die de Adobe Primetime DRM Java SDK of logboekberichten tijdens de tijd kunnen hebben geproduceerd dat de server is geïnitialiseerd.

### Partitielogbestand {#section_5660137CD6AA40519E72A4315534846B}

Het partitielogbestand, [!DNL flashaccess-partition.log], bevindt zich in de `<LicenseServer.LogRoot>/flashaccesserver` directory. Het omvat logboekberichten die tijdens de verwerking van een vergunningsverzoek zijn geproduceerd.

### Aanraaklogboek {#section_F0257CC0831647F18A746B4F02E3E910}

Logbestand van de huurder, [!DNL flashaccess-tenant.log], bevindt zich in `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. Het huurderslogboek omvat controleinformatie die elke vergunning beschrijft die voor deze huurder wordt geproduceerd.

## Configuratiebestanden bijwerken {#updating-configuration-files}

Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.

Wanneer u het configuratiebestand wijzigt, slaat de licentieserver de tijd op waarop het bestand voor het laatst is gewijzigd. Bij een configureerbaar interval controleert de server of de tijd van de bestandswijziging is gewijzigd. Als deze is gewijzigd, laadt de server automatisch de inhoud van het configuratiebestand opnieuw.

Als u wilt bepalen hoe vaak de server controleert op updates, moet u de `refreshDelaySeconds` in het dialoogvenster `Caching` -element van het algemene configuratiebestand. Als `refreshDelaySeconds` wordt geplaatst aan 3600 seconden, zal de server de configuratie binnen hoogstens één uur na de wijzigingstijd van het configuratiedossier bijwerken. Indien `refreshDelaySeconds` is ingesteld op 0, controleert de server op configuratieupdates bij elk verzoek. Het wordt afgeraden om `refreshDelaySeconds` tot een lage waarde in om het even welke productiemilieu&#39;s omdat het doen dit prestaties kan beïnvloeden.

De `Caching` element bepaalt ook hoeveel huurdersconfiguraties tegelijk in de cache worden geplaatst. U kunt deze waarde aan een aantal plaatsen dat kleiner is dan het totale aantal huurders om de hoeveelheid geheugen te beperken dat wordt gebruikt om de configuratieinformatie in het voorgeheugen onder te brengen. Als een verzoek voor een huurder wordt ontvangen die niet in het geheime voorgeheugen is, wordt de configuratie geladen alvorens het verzoek kan worden verwerkt. Als het geheime voorgeheugen volledig is, wordt de minst onlangs gebruikte huurder verwijderd uit het geheime voorgeheugen.

De cacheversie van de configuratie wordt in de volgende situaties (tot de volgende keer dat de server controleert op updates) nog steeds gebruikt:

* Als een wijziging wordt opgeslagen in een configuratiebestand of in een certificaatbestand waarnaar wordt verwezen in het dialoogvenster [!DNL flashaccess-tenant.xml] bestand als de server probeert het bestand te lezen
* Als de tijdstempel van het bestand minder dan één seconde voor de huidige tijd wordt gevonden
* Als de tijdstempel van het bestand in de toekomst wordt weergegeven

Als er geen versie in de cache is, mislukt het laden van de configuratie en wordt een fout geretourneerd aan de client. De server probeert dan om het dossier opnieuw te laden de volgende tijd het een verzoek voor die huurder ontvangt.

### Het algemene configuratiebestand bijwerken {#section_AA546C72442646CFB8906AEEBDF50587}

U kunt het HSM-wachtwoord wijzigen in [!DNL flashaccess-global.xml] op elk moment. De wijzigingen worden van kracht wanneer de server het configuratiebestand opnieuw laadt. Wijzigingen in de elementen Logging en Caching worden echter niet opnieuw geladen. U moet de server opnieuw starten voordat wijzigingen voor deze elementen van kracht worden.

### Het configuratiebestand van de huurder bijwerken {#section_71624DB8DF28480F84F34F0FF7FD4365}

U kunt alle waarden wijzigen die in het dialoogvenster [!DNL flashaccess-tenant.xml] op elk gewenst moment. De wijzigingen worden van kracht wanneer de server het configuratiebestand opnieuw laadt. De server controleert ook of er wijzigingen zijn aangebracht in alle referenties ( [!DNL .pfx]) bestanden en bestanden met het lijst van gewenste personen-certificaat van Packager die in het configuratiebestand voor de  van de huurder worden vermeld.
