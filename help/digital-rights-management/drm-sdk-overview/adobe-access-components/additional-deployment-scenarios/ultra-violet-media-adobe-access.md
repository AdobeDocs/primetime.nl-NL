---
title: UltraViolet-media en Adobe Primetime DRM
description: UltraViolet-media en Adobe Primetime DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# UltraViolet-media en Adobe Primetime DRM {#ultraviolet-media-and-adobe-primetime-drm}

Adobe Primetime DRM kan worden gebruikt in combinatie met andere oplossingen voor het streamen van inhoud van derden om een volledig en veilig, op DRM gebaseerd ecosysteem voor mediadistributie in te stellen.

UltraViolet is een digitaal rechtenverificatie- en cloudgebaseerd distributiesysteem dat consumenten van digitale home entertainment-inhoud in staat stelt gekochte inhoud te streamen en te downloaden via meerdere platforms en apparaten. De UltraViolet-inhoud wordt gedownload (of gestreamd) in een CFF (Common File Format) met behulp van Common Encryption (CENC).

Het is eenvoudig om een UltraViolet-systeem samen met Adobe Primetime DRM in te stellen. Het volgende gebruiksgeval geeft het gedrag van de inhoudsstroom weer:

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. De eigenaar van de inhoud codeert en verpakt de inhoud in CFF. De inhoud in het pakket wordt in licentie gegeven aan een detailhandelaar voor distributie.
1. De detailhandelaar uploadt de inhoud aan een digitale dienstverlener, zoals CDN. De inhoud kan nu worden gedownload. Sommige van deze rollen kunnen door één of meerdere bedrijven worden gespeeld.

   De eindgebruiker heeft een apparaat dat Adobe AIR ondersteunt. Bovendien moet de gebruiker een toepassing installeren die compatibel is met UltraViolet. De toepassing bevat de code die nodig is om de CFF te parseren en te presenteren voor gebruik door de runtime. Alle gevoelige cryptografische verrichtingen worden behandeld in veilige runtime.
1. De toepassing kan een domein teweegbrengen toetreedt voor het apparaat, dat met de coördinator in wisselwerking staat. De coördinator houdt een rechtenlocker, een gebruikersgegevensbestand en domeinen bij. De domeinmanager van de coördinator wordt gebouwd gebruikend Primetime DRM SDK om Primetime DRM-Specifieke domein uit te voeren toetreedt/verlaat verrichtingen.
1. De gebruiker kan de toepassing dan gebruiken om een video te selecteren die hij of zij van de detailhandelaar wil verkrijgen. De detailhandelaar verstrekt typisch een Webportaal en behandelt al bedrijfslogica.
1. De detailhandelaar communiceert dan met de coördinator om een rechtentoken toe te voegen. De detailhandelaar leidt dan het verzoek aan de dienstverlener voor de daadwerkelijke inhouddownload opnieuw.
1. Als het apparaat nog geen licentie voor de inhoud heeft, wordt een licentieaanvraag geactiveerd met behulp van de CFF. De aanvraag bevat doorgaans een domeincertificaat, gebruikersgegevens en informatie over de toepassing. De serviceprovider beheert een Primetime DRM-licentieserver (ontwikkeld met de Primetime DRM SDK) die voldoet aan de UltraViolet-specificaties.
1. De UltraViolet bedrijfslogica van de dienstverlener wisselt met de coördinator in zoals nodig om het aangewezen rechtenteken terug te winnen om te bepalen of een inhoudsvergunning zou moeten worden uitgegeven.

   De inhoudslicentie is gebonden aan het domein. De clienttoepassing kan de licentie in het CFF-bestand invoegen. Inhoud kan nu in de toepassing worden afgespeeld, waarbij alle beveiliging en handhaving van de gebruiksregel door de Primetime DRM-component in de runtime worden afgehandeld.
1. Andere apparaten en toepassingen die eigendom zijn van dezelfde eindgebruiker kunnen bij de coördinator worden geregistreerd. De inhoud kan nu in andere Primetime DRM-apparaten worden geladen zonder dat een externe transactie vereist is.
