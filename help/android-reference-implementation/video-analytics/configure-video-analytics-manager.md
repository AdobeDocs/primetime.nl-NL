---
description: U kunt het videogebruik bijhouden in de Primetime Android-naslagimplementatie door deze te configureren voor gebruik met uw Adobe Analytics-account.
title: Video-analyse configureren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Videoanalyse configureren {#configure-video-analytics}

U kunt het videogebruik bijhouden in de Primetime Android-naslagimplementatie door deze te configureren voor gebruik met uw Adobe Analytics-account. De Android Reference Implementation is ontworpen om videogebruik en hartslaggegevens naar Adobe Analytics te verzenden. Als u deze functie wilt inschakelen, moet u eerst contact opnemen met uw Adobe Primetime-vertegenwoordiger en een Adobe Analytics-account maken.

Er zijn twee plaatsen binnen de Implementatie van de Verwijzing die u moet vormen om de integratie van Adobe Analytics toe te laten. De configuraties van de runtime Video Analytics hebben invloed wanneer een nieuwe video voor playback wordt geselecteerd (d.w.z. zodra een nieuwe PlayerAction wordt gecreeerd).

1. Configureer opties voor de laadtijd in het elementbestand `ADBMobileConfig.json`.

   Dit bestand wordt geleverd door uw Adobe-vertegenwoordiger. Deze wordt standaard niet opgenomen in de Primetime SDK-bundel. Zie hier de Android-programmahandleiding voor meer informatie over de instellingen in dit configuratiebestand: Initialiseer en configureer videoanalyses.
1. Uitvoeringsopties configureren in het menu Referentie-instellingen voor implementatie

   ![](assets/img_psdk_ref_impl_va-settings-menu.png)

   | Uitvoeringsopties | Beschrijving |
   |---|---|
   | Video Analytics tracking-server | URL van het eindpunt van de verzameling voor videoanalytische back-endgegevens. Dit is waar alle video hartslag het volgen vraag wordt verzonden. |
   | Taak-id | De id van de verwerkingstaak. Dit wijst op het achterste eindpunt dat soort verwerking om voor video-volgende vraag van toepassing te zijn. |
   | Kanaal | De naam van het kanaal waar de gebruiker de inhoud bekijkt. Voor een mobiele toepassing is dit doorgaans de naam van de toepassing. |
   | Uitgever | De naam van de uitgever van de inhoud |
   | Foutopsporingsregistratie | Hiermee activeert u uitgebreide logboekregistratie. Deze optie is standaard uitgeschakeld en kan van invloed zijn op de prestaties wanneer deze zijn ingeschakeld. U schakelt deze optie dus uit voor een productieomgeving. |
   | Quiet-modus | Wanneer dit wordt toegelaten, worden geen netwerkvraag gemaakt, zodat zou dit voor lokaal het zuiveren nuttig zijn, maar moet voor een productiemilieu worden onbruikbaar gemaakt. |