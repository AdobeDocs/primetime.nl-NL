---
description: Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.
seo-description: Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.
seo-title: Configuratiebestanden bijwerken
title: Configuratiebestanden bijwerken
uuid: 34b3247c-3458-49de-b1b0-dc0ebbf61c88
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---


# Configuratiebestanden{#updating-configuration-files} bijwerken

Zodra de licentieserver een van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elke licentieaanvraag. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden.

Wanneer u het configuratiebestand wijzigt, slaat de licentieserver de tijd op waarop het bestand voor het laatst is gewijzigd. Bij een configureerbaar interval controleert de server of de tijd van de bestandswijziging is gewijzigd. Als deze is gewijzigd, laadt de server automatisch de inhoud van het configuratiebestand opnieuw.

Als u wilt bepalen hoe vaak de server controleert op updates, moet u het `refreshDelaySeconds` attribuut in het `Caching` element van het globale configuratiedossier plaatsen. Als `refreshDelaySeconds` bijvoorbeeld is ingesteld op 3600 seconden, werkt de server de configuratie binnen maximaal één uur na de wijzigingstijd van het configuratiebestand bij. Als `refreshDelaySeconds` is ingesteld op 0, controleert de server op elke aanvraag op updates van de configuratie. Het wordt afgeraden `refreshDelaySeconds` in te stellen op een lage waarde in een productieomgeving, omdat dit van invloed kan zijn op de prestaties.

Het element `Caching` bepaalt ook hoeveel configuraties van huurders tegelijk in de cache worden geplaatst. U kunt deze waarde aan een aantal plaatsen dat kleiner is dan het totale aantal huurders om de hoeveelheid geheugen te beperken dat wordt gebruikt om de configuratieinformatie in het voorgeheugen onder te brengen. Als een verzoek voor een huurder wordt ontvangen die niet in het geheime voorgeheugen is, wordt de configuratie geladen alvorens het verzoek kan worden verwerkt. Als het geheime voorgeheugen volledig is, wordt de minst onlangs gebruikte huurder verwijderd uit het geheime voorgeheugen.

De cacheversie van de configuratie wordt in de volgende situaties (tot de volgende keer dat de server controleert op updates) nog steeds gebruikt:

* Als een wijziging wordt opgeslagen in een configuratiebestand of in een van de certificaatbestanden waarnaar wordt verwezen in het [!DNL flashaccess-tenant.xml]-bestand terwijl de server probeert het bestand te lezen
* Als de tijdstempel van het bestand minder dan één seconde voor de huidige tijd wordt gevonden
* Als de tijdstempel van het bestand in de toekomst wordt weergegeven

Als er geen versie in de cache is, mislukt het laden van de configuratie en wordt een fout geretourneerd aan de client. De server probeert dan om het dossier opnieuw te laden de volgende tijd het een verzoek voor die huurder ontvangt.

## Het algemene configuratiebestand {#section_AA546C72442646CFB8906AEEBDF50587} bijwerken

U kunt het wachtwoord HSM in [!DNL flashaccess-global.xml] op elk ogenblik wijzigen. De wijzigingen worden van kracht wanneer de server het configuratiebestand opnieuw laadt. Wijzigingen in de elementen Logging en Caching worden echter niet opnieuw geladen. U moet de server opnieuw starten voordat wijzigingen voor deze elementen van kracht worden.

## Het bijwerken van het dossier van de huurdersconfiguratie {#section_71624DB8DF28480F84F34F0FF7FD4365}

U kunt op elk gewenst moment alle waarden wijzigen die in het [!DNL flashaccess-tenant.xml]-bestand zijn opgegeven. De wijzigingen worden van kracht wanneer de server het configuratiebestand opnieuw laadt. De server controleert ook of er wijzigingen zijn aangebracht in alle referentiebestanden ( [!DNL .pfx]) en pakketbestanden met het certificaatcertificaat van de lijst van gewenste personen die in het configuratiebestand van de huurder worden vermeld.
