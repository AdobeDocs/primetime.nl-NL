---
seo-title: De referentieimplementatiedatabase bijwerken
title: De referentieimplementatiedatabase bijwerken
uuid: 2883045e-ad62-466d-94a2-fc45ded2a4f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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
