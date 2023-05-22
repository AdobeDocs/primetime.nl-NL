---
description: Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.
title: Configuratiebestanden bijwerken
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---


# Configuratiebestanden bijwerken{#updating-configuration-files}

Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.

Wanneer u het configuratiebestand wijzigt, slaat de licentieserver de tijd op waarop het bestand voor het laatst is gewijzigd. Bij een configureerbaar interval controleert de server of de tijd van de bestandswijziging is gewijzigd. Als deze is gewijzigd, laadt de server automatisch de inhoud van het configuratiebestand opnieuw.

Als u wilt bepalen hoe vaak de server controleert op updates, moet u de `refreshDelaySeconds` in het dialoogvenster `Caching` -element van het algemene configuratiebestand. Als `refreshDelaySeconds` wordt geplaatst aan 3600 seconden, zal de server de configuratie binnen hoogstens één uur na de wijzigingstijd van het configuratiedossier bijwerken. Indien `refreshDelaySeconds` is ingesteld op 0, controleert de server op configuratieupdates bij elk verzoek. Het wordt afgeraden om `refreshDelaySeconds` tot een lage waarde in om het even welke productiemilieu&#39;s omdat het doen van dit prestaties kan beïnvloeden.

De `Caching` element bepaalt ook hoeveel huurdersconfiguraties tegelijk in de cache worden geplaatst. U kunt deze waarde aan een aantal plaatsen dat kleiner is dan het totale aantal huurders om de hoeveelheid geheugen te beperken dat wordt gebruikt om de configuratieinformatie in het voorgeheugen onder te brengen. Als een verzoek voor een huurder wordt ontvangen die niet in het geheime voorgeheugen is, wordt de configuratie geladen alvorens het verzoek kan worden verwerkt. Als het geheime voorgeheugen volledig is, wordt de minst onlangs gebruikte huurder verwijderd uit het geheime voorgeheugen.

De cacheversie van de configuratie wordt in de volgende situaties (tot de volgende keer dat de server controleert op updates) nog steeds gebruikt:

* Als een wijziging wordt opgeslagen in een configuratiebestand of in een certificaatbestand waarnaar wordt verwezen in het dialoogvenster [!DNL flashaccess-tenant.xml] bestand als de server probeert het bestand te lezen
* Als de tijdstempel van het bestand minder dan één seconde voor de huidige tijd wordt gevonden
* Als de tijdstempel van het bestand in de toekomst wordt weergegeven

Als er geen versie in de cache is, mislukt het laden van de configuratie en wordt een fout geretourneerd aan de client. De server probeert dan om het dossier opnieuw te laden de volgende tijd het een verzoek voor die huurder ontvangt.

## Het algemene configuratiebestand bijwerken {#section_AA546C72442646CFB8906AEEBDF50587}

U kunt het HSM-wachtwoord wijzigen in [!DNL flashaccess-global.xml] op elk moment. De wijzigingen worden van kracht wanneer de server het configuratiebestand opnieuw laadt. Wijzigingen in de elementen Logging en Caching worden echter niet opnieuw geladen. U moet de server opnieuw starten voordat wijzigingen voor deze elementen van kracht worden.

## Het configuratiebestand van de huurder bijwerken {#section_71624DB8DF28480F84F34F0FF7FD4365}

U kunt alle waarden wijzigen die zijn opgegeven in het dialoogvenster [!DNL flashaccess-tenant.xml] op elk gewenst moment. De wijzigingen worden van kracht wanneer de server het configuratiebestand opnieuw laadt. De server controleert ook of er wijzigingen zijn aangebracht in alle referenties ( [!DNL .pfx]) bestanden en pakketbestanden met lijsten van gewenste personen-certificaten waarnaar wordt verwezen in het configuratiebestand van de huurder.
