---
title: De referentieimplementatiedatabase bijwerken
description: De referentieimplementatiedatabase bijwerken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# De referentieimplementatiedatabase bijwerken{#update-the-reference-implementation-db}

Om gebruiksmodellen te controleren waaronder een vergunning aan een aangewezen gebruiker wordt verleend, voeg ingangen aan het gegevensbestand van de verwijzings implementatie toe.

1. Voeg vermeldingen toe aan de `Customer` tabel.

   De `Customer` de lijst omvat gebruikersnamen en wachtwoorden om gebruikers voor authentiek te verklaren. Het geeft ook aan of een gebruiker een abonnement heeft (een licentie die is uitgegeven onder de *Abonnement* gebruiksmodel).

1. Bied een gebruiker toegang via de gebruiksmodellen Downloaden naar het eigen systeem of Video op aanvraag.

       Voeg vermeldingen toe aan de tabel &quot;CustomerAuthorization&quot; om aan te geven:
   
   * Het gebruiksmodel
   * Elk segment met inhoud waartoe een gebruiker toegang heeft

Voor meer informatie over hoe te om elke lijst te bevolken, zie [!DNL PopulateSampleDB.sql] script (opgenomen op uw Primetime DRM-dvd in het dialoogvenster [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] directory).
