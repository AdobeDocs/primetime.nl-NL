---
title: Toezicht
description: Toezicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Toezicht{#monitoring}

De server van de Individualisering en de Zeer belangrijke server van de Generatie elk hebben een statuspagina, die u kunt gebruiken om de gezondheid van de servers te bepalen.

* **Afzonderlijke statuspagina:** [!DNL https://SERVER:PORT/flashaccess/status]

   * Meldt &quot;Alive&quot; als de toepassingsserver wordt uitgevoerd en de app een aanvraag voor een GET kan indienen bij de server voor sleutelgeneratie.
   * De pagina rapporteert &quot;Alive&quot; of niets. Er wordt geen informatie over de toepassing weergegeven. Deze pagina kan dus worden gebruikt voor controle van buiten de firewall.

* **Statuspagina voor sleutelgeneratie:** [!DNL https://SERVER:PORT/flashaccess-kgs/status]

   * Meldt &quot;Alive&quot; als de toepassingsserver wordt uitgevoerd
   * Alle URL&#39;s voor sleutelgeneratie moeten alleen intern toegankelijk zijn

* **Pagina Afzonderlijke statistieken:** [!DNL https://SERVER:PORT/flashaccess/admin/appstats]

   * Omvat statistieken over de server van de Individualisering, zoals aantal gediende verzoeken en het aantal sleutels beschikbaar in het geheime voorgeheugen
   * Deze pagina mag alleen intern toegankelijk zijn

* **De belangrijkste pagina van de Statistieken van de Generatie:** [!DNL https://SERVER:PORT/flashaccess-kgs/appstats]

   * Omvat statistieken over de Zeer belangrijke server van de Generatie, zoals het aantal gediende verzoeken en het aantal zeer belangrijke dossiers beschikbaar op schijf
   * Alle URL&#39;s voor sleutelgeneratie moeten alleen intern toegankelijk zijn
