---
title: Apparaatmogelijkheden vereist om beveiligde inhoud af te spelen
description: Apparaatmogelijkheden vereist om beveiligde inhoud af te spelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Apparaatmogelijkheden vereist om beveiligde inhoud af te spelen {#device-capabilities-required-to-play-protected-content}

De vereiste apparaatmogelijkheden geven de hardwaremogelijkheden aan die vereist zijn voor toegang tot inhoud. Informatie over de hardwaremogelijkheden is beschikbaar voor apparaten die de portkit gebruiken.

De volgende kenmerken kunnen de mogelijkheden van het apparaat identificeren:

<table id="table_v3n_fks_n4"> 
 <tbody> 
  <tr> 
   <td><b>Kenmerk</b> </td> 
   <td><b>Ondersteunde waarden</b> </td> 
   <td><b>Criteria afstemmen</b> </td> 
   <td><b>Beschrijving</b> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Niet-gebruikerstoegankelijke bus </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true" of "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Exacte overeenkomst </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Indien waar (true), mag het apparaat geen voor de gebruiker toegankelijke bus hebben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Hoofdmap van vertrouwen voor hardware </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true" of "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Exacte overeenkomst </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Indien waar (true), moet het apparaat beschikken over een vertrouwenwekkende hardwarebron. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Deze gebruiksregel wordt ondersteund door Adobe Primetime DRM-clients versie 2.0.2 en hoger. Het gedrag bij oudere clients is afhankelijk van de minimale clientversie die door de licentieserver wordt ondersteund.
>
>Zie [Minimale clientversie](../../../../protecting-content/setting-up-the-sdk/setup-dev-env.md).
