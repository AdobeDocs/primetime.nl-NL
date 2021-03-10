---
title: De referentieimplementatiedatabase bijwerken
description: De referentieimplementatiedatabase bijwerken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# De referentie-implementatie-DB{#update-the-reference-implementation-db} bijwerken

Om gebruiksmodellen te controleren waaronder een vergunning aan een aangewezen gebruiker wordt verleend, voeg ingangen aan het gegevensbestand van de verwijzings implementatie toe.

1. Voeg items toe aan de tabel `Customer`.

   De tabel `Customer` bevat gebruikersnamen en wachtwoorden om gebruikers te verifiëren. Ook wordt aangegeven of een gebruiker een abonnement heeft (een licentie die is uitgegeven onder het gebruiksmodel *Subscription*).

1. Bied een gebruiker toegang via de gebruiksmodellen Downloaden naar het eigen systeem of Video op aanvraag.

       Voeg vermeldingen toe aan de tabel &quot;CustomerAuthorization&quot; om aan te geven:
   
   * Het gebruiksmodel
   * Elk segment met inhoud waartoe een gebruiker toegang heeft

Voor meer informatie over hoe te om elke lijst te bevolken, zie [!DNL PopulateSampleDB.sql] manuscript (inbegrepen op uw Dvd van Primetime DRM in [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] folder).
