---
description: De Toegang van de Adobe kan met andere derdeinhoud worden gebruikt die oplossingen stromen om een volledig en veilig op DRM-Gebaseerd media distributiecosysteem op te zetten.
title: Ultraviolet-media en toegang tot Adobe
exl-id: cca476a4-1961-46d8-aad4-bc7c996d7b02
source-git-commit: 8d7a4f69a6400b0c3242d4cb0c5daac81f27db3a
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Ultraviolet-media en toegang tot Adobe {#ultraviolet-media-and-adobe-access}

De Toegang van de Adobe kan met andere derdeinhoud worden gebruikt die oplossingen stromen om een volledig en veilig op DRM-Gebaseerd media distributiecosysteem op te zetten.

UltraViolet is een digitaal rechtenverificatie- en cloudgebaseerd distributiesysteem dat consumenten van digitale home entertainment-inhoud in staat stelt gekochte inhoud te streamen en te downloaden via meerdere platforms en apparaten. De UltraViolet-inhoud wordt gedownload (of gestreamd) in een CFF (Common File Format) met behulp van Common Encryption (CENC).

Het is eenvoudig om een UltraViolet-systeem samen met Adobe Access in te stellen. Het volgende gebruiksgeval geeft het gedrag van de inhoudsstroom weer:

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. De eigenaar van de inhoud codeert en verpakt de inhoud in CFF. De inhoud in het pakket wordt in licentie gegeven aan een detailhandelaar voor distributie.
1. De detailhandelaar uploadt de inhoud aan een digitale dienstverlener, zoals CDN. De inhoud kan nu worden gedownload. Merk op dat sommige van deze rollen door één of meerdere bedrijven kunnen worden gespeeld.

   De eindgebruiker heeft een apparaat dat Adobe AIR ondersteunt. Daarnaast moet de gebruiker een toepassing installeren die compatibel is met UltraViolet. De toepassing bevat de code die nodig is om de CFF te parseren en te presenteren voor gebruik door de runtime. Alle gevoelige cryptografische verrichtingen worden behandeld in veilige runtime.
1. De toepassing kan een domein teweegbrengen toetreedt voor het apparaat, dat met de coördinator in wisselwerking staat. De coördinator handhaaft een rechtenlocker, een gebruikersgegevensbestand en domeinen. De het domeinmanager van de coördinator wordt gebouwd gebruikend de Toegang SDK van de Adobe om Adobe toegang-specifieke domein uit te voeren toetreedt/verlaat verrichtingen.
1. De gebruiker kan de toepassing dan gebruiken om een video te selecteren die hij of zij van de detailhandelaar wil verkrijgen. De detailhandelaar verstrekt typisch een Webportaal en behandelt al bedrijfslogica.
1. De detailhandelaar werkt dan met de coördinator in wisselwerking om een rechtenteken toe te voegen. De detailhandelaar leidt dan het verzoek aan de dienstverlener voor de daadwerkelijke inhouddownload opnieuw.
1. Als het apparaat nog geen licentie voor de inhoud heeft, wordt een licentieaanvraag geactiveerd met behulp van de CFF. De aanvraag bevat doorgaans een domeincertificaat, gebruikersgegevens en informatie over de toepassing. De dienstverlener stelt een Server van de Vergunning van de Toegang van de Adobe (die gebruikend de Toegang SDK van de Adobe wordt ontwikkeld) in werking die de specificaties UltraViolet volgt.
1. De UltraViolet bedrijfslogica van de dienstverlener wisselt met de coördinator in zoals nodig om het aangewezen rechtenteken terug te winnen om te bepalen of een inhoudsvergunning zou moeten worden uitgegeven.

   De inhoudslicentie is gebonden aan het domein. De clienttoepassing kan de licentie in het CFF-bestand invoegen. Inhoud kan nu worden afgespeeld in de toepassing, waarbij alle beveiliging en handhaving van de gebruiksregel worden afgehandeld door de component Adobe Access in de runtime.
1. Andere apparaten en toepassingen die eigendom zijn van dezelfde eindgebruiker kunnen bij de coördinator worden geregistreerd. De inhoud kan nu in andere apparaten van de Toegang van de Adobe worden geladen zonder enige externe transactie te vereisen.
