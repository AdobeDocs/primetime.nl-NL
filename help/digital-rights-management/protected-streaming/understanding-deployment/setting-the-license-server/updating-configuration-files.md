---
description: Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.
seo-description: Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.
seo-title: Configuratiebestanden bijwerken
title: Configuratiebestanden bijwerken
uuid: 34b3247c-3458-49de-b1b0-dc0ebbf61c88
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuratiebestanden bijwerken{#updating-configuration-files}

Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.

Wanneer u het configuratiebestand wijzigt, slaat de licentieserver de tijd op waarop het bestand voor het laatst is gewijzigd. Bij een configureerbaar interval controleert de server of de tijd van de bestandswijziging is gewijzigd. Als deze is gewijzigd, laadt de server automatisch de inhoud van het configuratiebestand opnieuw.

Als u wilt controleren hoe vaak de server op updates controleert, moet u de `refreshDelaySeconds` attributen in het `Caching` element van het globale configuratiedossier plaatsen. Bijvoorbeeld, als `refreshDelaySeconds` aan 3600 seconden wordt geplaatst, zal de server de configuratie binnen hoogstens één uur na de wijzigingstijd van het configuratiedossier bijwerken. Als `refreshDelaySeconds` is ingesteld op 0, controleert de server op elke aanvraag op configuratietoepassingen. Het wordt afgeraden een lage waarde in te stellen `refreshDelaySeconds` in productieomgevingen, omdat dit van invloed kan zijn op de prestaties.

Het `Caching` element bepaalt ook hoeveel huurdersconfiguraties tegelijk in de cache worden geplaatst. U kunt deze waarde aan een aantal plaatsen dat kleiner is dan het totale aantal huurders om de hoeveelheid geheugen te beperken dat wordt gebruikt om de configuratieinformatie in het voorgeheugen onder te brengen. Als een verzoek voor een huurder wordt ontvangen die niet in het geheime voorgeheugen is, wordt de configuratie geladen alvorens het verzoek kan worden verwerkt. Als het geheime voorgeheugen volledig is, wordt de minst onlangs gebruikte huurder verwijderd uit het geheime voorgeheugen.

De cacheversie van de configuratie wordt in de volgende situaties (tot de volgende keer dat de server controleert op updates) nog steeds gebruikt:

* Als een wijziging wordt opgeslagen in een configuratiebestand of in een van de certificaatbestanden waarnaar in het [!DNL flashaccess-tenant.xml] bestand wordt verwezen terwijl de server het bestand probeert te lezen
* Als de tijdstempel van het bestand minder dan één seconde voor de huidige tijd wordt gevonden
* Als de tijdstempel van het bestand in de toekomst wordt weergegeven

Als er geen versie in de cache is, mislukt het laden van de configuratie en wordt een fout geretourneerd aan de client. De server probeert dan om het dossier opnieuw te laden de volgende tijd het een verzoek voor die huurder ontvangt.

## Het algemene configuratiebestand bijwerken {#section_AA546C72442646CFB8906AEEBDF50587}

U kunt het wachtwoord HSM op elk [!DNL flashaccess-global.xml] ogenblik wijzigen. De wijzigingen worden van kracht wanneer de server het configuratiebestand opnieuw laadt. Wijzigingen in de elementen Logging en Caching worden echter niet opnieuw geladen. U moet de server opnieuw starten voordat wijzigingen voor deze elementen van kracht worden.

## Het configuratiebestand van de huurder bijwerken {#section_71624DB8DF28480F84F34F0FF7FD4365}

U kunt op elk gewenst moment alle waarden wijzigen die in het [!DNL flashaccess-tenant.xml] bestand zijn opgegeven. De wijzigingen worden van kracht wanneer de server het configuratiebestand opnieuw laadt. Ook, controleert de server om het even welke wijzigingen in alle referentie ( [!DNL .pfx]) dossiers en pakketwhitelist certificaatdossiers die in het dossier van de huurdersconfiguratie van verwijzingen worden voorzien.
