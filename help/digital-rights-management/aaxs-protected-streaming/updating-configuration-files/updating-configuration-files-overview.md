---
title: Overzicht van configuratiebestanden bijwerken
description: Overzicht van configuratiebestanden bijwerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Overzicht van configuratiebestanden bijwerken {#updating-configuration-files-overview}

Zodra de licentieserver één van de configuratiebestanden van de licentieserver (algemene configuratie of huurdersconfiguratie) leest, wordt de configuratiegegevens in het geheugen opgeslagen. Daarom hoeven de bestanden niet van schijf te worden gelezen voor elk licentieverzoek. De server staat echter ook toe dat de meeste waarden in de configuratiebestanden worden gewijzigd zonder dat een server opnieuw moet worden opgestart om de wijzigingen van kracht te laten worden. (Zie hieronder voor meer informatie over welke configuratiewaarden op updates worden gecontroleerd.)

Als u de configuratie opnieuw wilt laden wanneer er wijzigingen worden aangebracht, slaat de licentieserver de tijd op waarop het bestand voor het laatst is gewijzigd. Bij een configureerbaar interval controleert de server of de tijd van de bestandswijziging is gewijzigd en, als dat het geval is, laadt de server de inhoud van het bestand opnieuw.

Als u wilt bepalen hoe vaak de server controleert op updates, stelt u de optie `refreshDelaySeconds` kenmerk in het element Caching van het algemene configuratiebestand. Als `refreshDelaySeconds` is ingesteld op 3600 seconden, duurt het maximaal één uur vanaf het moment dat het bestand wordt bijgewerkt voordat de configuratietoepassingen door de server worden gedetecteerd. Indien `refreshDelaySeconds` is ingesteld op 0, controleert de server op configuratieupdates voor elk verzoek. Instelling `refreshDelaySeconds` voor een lage waarde wordt niet aanbevolen voor productieomgevingen, omdat dit van invloed kan zijn op de prestaties.

Het element Caching bepaalt ook hoeveel huurdersconfiguraties tegelijkertijd in de cache worden geplaatst. U kunt deze waarde aan een aantal plaatsen kleiner dan het totale aantal huurders om de hoeveelheid geheugen te beperken die wordt gebruikt om de configuratieinformatie in het voorgeheugen onder te brengen. Als een verzoek voor een huurder niet in het geheime voorgeheugen wordt ontvangen, wordt de configuratie geladen alvorens het verzoek kan worden verwerkt. Als het geheime voorgeheugen volledig is, wordt de minst onlangs gebruikte huurder verwijderd uit het geheime voorgeheugen.

Als een wijziging wordt opgeslagen in een configuratiebestand of in een certificaatbestand waarnaar wordt verwezen in [!DNL flashaccess-tenant.xml] terwijl de server probeert het bestand te lezen, of als de tijdstempel van het bestand minder dan één seconde voor de huidige tijd of in de toekomst is, wordt de in cache opgeslagen versie van de configuratie gebruikt tot de volgende keer dat de server controleert op updates. Als er geen versie in de cache is, mislukt het laden van de configuratie en wordt een fout geretourneerd aan de client. De server probeert om het dossier opnieuw te laden de volgende keer het een verzoek voor die huurder ontvangt.
