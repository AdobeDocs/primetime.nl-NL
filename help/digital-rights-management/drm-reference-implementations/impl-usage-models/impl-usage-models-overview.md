---
description: 'null'
seo-description: 'null'
seo-title: Overzicht
title: Overzicht
uuid: 5f82f603-6e2d-4c9d-a49f-7b07f30a29e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Overzicht{#overview}

De implementatie van de Verwijzing omvat een demomodus optie die aantoont hoe te om verschillende gebruiksmodellen voor een segment van verpakte inhoud uit te voeren. In de demomodus wordt bedrijfslogica voor deze gebruiksmodellen gebruikt:

* **Download-To-Own (DTO)**  - Gebruikers kunnen de inhoud online of offline downloaden en krijgen een permanente licentie voor de inhoud.
* **Huur/Video-On-Demand (VOD)**  - De beschikbare inhoud wordt geleverd met op tijd gebaseerde beperkingen. Gebruikers kunnen de inhoud bijvoorbeeld gedurende een periode van 30 dagen afspelen. Wanneer het afspelen begint, kan de gebruiker maximaal 48 uur de tijd hebben om het bekijken van de inhoud te voltooien. De inhoud moet over 30 dagen worden bekeken.
* **Abonnement (alles-u-kan-eet)**  - sommige diensten bieden betaalde abonnementen aan die gebruikers onbeperkte toegang tot een grote bibliotheek van inhoud geven zolang zij een maandtarief blijven betalen. De licentieserver geeft een unieke licentie voor elk inhoudssegment uit en geeft ook een hoofdlicentie uit die aan het einde van de abonnementsperiode verloopt. Elke maand, wanneer de gebruikers hun abonnement vernieuwen, moet de wortelvergunning ook worden vernieuwd.

   >[!NOTE]
   >
   >Voor de voorafgaande gebruiksmodellen, na het verwerven van een vergunning, moeten de gebruikers hun geloofsbrieven ingaan zodat de server kan verifiëren dat de gebruikers een huurrekening hebben.

* **Door ad-funding**  - De inhoud wordt geleend door reclame op te nemen als onderdeel van de ervaring. Met dit model, kan de inhoud worden verdeeld en vereist geen gebruikersauthentificatie.

In de demomodus van het gebruiksmodel bepaalt de bedrijfslogica op de server de kenmerken voor gegenereerde licenties. Tijdens het verpakken moet uw DRM-beleid alleen aangeven of verificatie vereist is.

Om alle vier gebruiksmodellen toe te laten, moet u slechts twee beleid DRM omvatten:

* Één beleid DRM dat anonieme toegang voor het Adf-gefinancierde model toestaat
* Één beleid DRM dat gebruikersnaam/wachtwoordauthentificatie voor de andere drie gebruiksmodellen vereist.

Wanneer een gebruiker om een vergunning verzoekt, kan een cliënttoepassing bepalen of om de gebruiker voor authentificatie te vragen die op de authentificatieinformatie in het beleid DRM wordt gebaseerd.
