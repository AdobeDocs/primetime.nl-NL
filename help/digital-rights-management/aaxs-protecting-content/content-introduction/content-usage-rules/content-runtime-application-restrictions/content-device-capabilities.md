---
title: Apparaatmogelijkheden vereist om beveiligde inhoud af te spelen
description: Apparaatmogelijkheden vereist om beveiligde inhoud af te spelen
copied-description: true
exl-id: 5f2089e9-3176-46a7-9998-2dad0e77e453
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Apparaatmogelijkheden vereist om beveiligde inhoud af te spelen {#device-capabilities-required-to-play-protected-content}

Hiermee geeft u de hardwaremogelijkheden op die nodig zijn voor toegang tot inhoud. Informatie over de hardwaremogelijkheden is beschikbaar voor apparaten die de portkit gebruiken.

De mogelijkheden van het apparaat kunnen worden geïdentificeerd aan de hand van de kenmerken die in de volgende tabel worden vermeld:

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
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Exacte macro </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Indien waar (true), moet het apparaat een vertrouwensbasis voor de hardware hebben. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Deze gebruiksregel wordt gesteund door de cliëntversie 2.0.2 van de Toegang van de Adobe. Het gedrag bij oudere clients is afhankelijk van de minimale clientversie die door de licentieserver wordt ondersteund. Zie, [Minimale clientversie](../../../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md).
