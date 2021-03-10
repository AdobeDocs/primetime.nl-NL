---
description: Adobe Access kan worden gebruikt met andere oplossingen voor het streamen van inhoud van derden om een volledig en veilig, op DRM gebaseerd ecosysteem voor mediadistributie in te stellen.
title: UltraViolet-media en Adobe Access
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---


# UltraViolet media en Adobe Access {#ultraviolet-media-and-adobe-access}

Adobe Access kan worden gebruikt met andere oplossingen voor het streamen van inhoud van derden om een volledig en veilig, op DRM gebaseerd ecosysteem voor mediadistributie in te stellen.

UltraViolet ( [](https://www.uvvu.com/)) is een digitaal rechtenverificatie- en cloudgebaseerd distributiesysteem dat consumenten van digitale home entertainment-inhoud in staat stelt gekochte inhoud te streamen en te downloaden via meerdere platforms en apparaten. De UltraViolet-inhoud wordt gedownload (of gestreamd) in een CFF (Common File Format) met behulp van Common Encryption (CENC).

Het is eenvoudig om een UltraViolet-systeem samen met Adobe Access in te stellen. Het volgende gebruiksgeval geeft het gedrag van de inhoudsstroom weer:

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. De eigenaar van de inhoud codeert en verpakt de inhoud in CFF. De inhoud in het pakket wordt in licentie gegeven aan een detailhandelaar voor distributie.
1. De detailhandelaar uploadt de inhoud aan een digitale dienstverlener, zoals CDN. De inhoud kan nu worden gedownload. Merk op dat sommige van deze rollen door één of meerdere bedrijven kunnen worden gespeeld.

   De eindgebruiker heeft een apparaat dat Adobe AIR ondersteunt. Daarnaast moet de gebruiker een toepassing installeren die compatibel is met UltraViolet. De toepassing bevat de code die nodig is om de CFF te parseren en te presenteren voor gebruik door de runtime. Alle gevoelige cryptografische verrichtingen worden behandeld in veilige runtime.
1. De toepassing kan een domein teweegbrengen toetreedt voor het apparaat, dat met de coördinator in wisselwerking staat. De coördinator handhaaft een rechtenlocker, een gebruikersgegevensbestand en domeinen. De het domeinmanager van de coördinator wordt gebouwd gebruikend de Adobe Toegang SDK om Adobe toegang-specifieke domein uit te voeren toetreedt/verlaat verrichtingen.
1. De gebruiker kan de toepassing dan gebruiken om een video te selecteren die hij of zij van de detailhandelaar wil verkrijgen. De detailhandelaar verstrekt typisch een Webportaal en behandelt al bedrijfslogica.
1. De detailhandelaar werkt dan met de coördinator in wisselwerking om een rechtenteken toe te voegen. De detailhandelaar leidt dan het verzoek aan de dienstverlener voor de daadwerkelijke inhouddownload opnieuw.
1. Als het apparaat nog geen licentie voor de inhoud heeft, wordt een licentieaanvraag geactiveerd met behulp van de CFF. De aanvraag bevat doorgaans een domeincertificaat, gebruikersgegevens en informatie over de toepassing. De serviceprovider beheert een Adobe Access-licentieserver (ontwikkeld met de Adobe Access SDK) die voldoet aan de UltraViolet-specificaties.
1. De UltraViolet bedrijfslogica van de dienstverlener wisselt met de coördinator in zoals nodig om het aangewezen rechtenteken terug te winnen om te bepalen of een inhoudsvergunning zou moeten worden uitgegeven.

   De inhoudslicentie is gebonden aan het domein. De clienttoepassing kan de licentie in het CFF-bestand invoegen. Inhoud kan nu worden afgespeeld in de toepassing, waarbij alle beveiliging en handhaving van de gebruiksregel worden afgehandeld door de component Adobe Access in de runtime.
1. Andere apparaten en toepassingen die eigendom zijn van dezelfde eindgebruiker kunnen bij de coördinator worden geregistreerd. De inhoud kan nu in andere apparaten van de Toegang van Adobe worden geladen zonder enige externe transactie te vereisen.

