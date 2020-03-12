---
seo-title: De referentieimplementatiedatabase bijwerken
title: De referentieimplementatiedatabase bijwerken
uuid: 2883045e-ad62-466d-94a2-fc45ded2a4f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# De referentieimplementatiedatabase bijwerken{#update-the-reference-implementation-db}

Om gebruiksmodellen te controleren waaronder een vergunning aan een aangewezen gebruiker wordt verleend, voeg ingangen aan het gegevensbestand van de verwijzings implementatie toe.

1. Voeg vermeldingen toe aan de `Customer` tabel.

   De `Customer` tabel bevat gebruikersnamen en wachtwoorden om gebruikers te verifiëren. Het geeft ook aan of een gebruiker een abonnement heeft (een licentie die is uitgegeven onder het gebruiksmodel *Abonnement* ).

1. Bied een gebruiker toegang via de gebruiksmodellen Downloaden naar het eigen systeem of Video op aanvraag.

       Voeg vermeldingen toe aan de tabel &quot;CustomerAuthorization&quot; om aan te geven:
   
   * Het gebruiksmodel
   * Elk segment met inhoud waartoe een gebruiker toegang heeft

Zie het [!DNL PopulateSampleDB.sql] script (opgenomen op uw Primetime DRM-dvd in de [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] directory) voor meer informatie over hoe u elke tabel kunt vullen.
