---
seo-title: Servereigenschappen
title: Servereigenschappen
uuid: 3d3a0ee3-009f-4d62-9587-7e487ecdcafd
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Servereigenschappen {#server-properties-files}

Voor de server zijn twee configuratiebestanden nodig: een voor de licentieserver en een voor de pakketsoftware. Beide bestanden moeten op het klassepad worden geplaatst. De eigenschappenbestanden bevatten de locatie van de gegevens die door Adobe zijn uitgegeven. Deze referenties kunnen worden opgegeven als een .pfx-bestand en wachtwoord of door een alias en wachtwoord op te geven voor een referentie die is opgeslagen op een HSM.

Raadpleeg de eigenschappenbestanden voor meer informatie over de specifieke waarden en het gebruik van elke parameter. Voorbeeldbestanden met eigenschappen vindt u in de map &quot;resources&quot; van de referentie-implementatie (Referentie Implementation\Server\resources).

Om de veiligheid van het wachtwoord van uw referentie te verzekeren, wordt een hulpmiddel verstrekt (ScrambleUtil.class) om het wachtwoord te coderen alvorens het in het flashaccess-refimpl.properties of flashaccess-refimpl-packager.properties- dossier is ingegaan.

Het wachtwoord van uw referentie op de juiste wijze voorbereiden:

1. Ga naar [!DNL Reference Implementation\Server\refimpl\scrambler].
1. Van de bevelherinnering, ga het bevel in:

   ```
   java -classpath  
   <i class="+ topic ph hi-d="" i "="">
   path_to_adobe-flashaccess-sdk.jar.; 
        com.adobe.flashaccess.refimpl.util.ScrambleUtil " 
   <i class="+ topic ph hi-d="" i "="">
   your_pfx_password" 
   </i class="+ topic> 
   </i class="+ topic>
   ```

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>In het vorige voorbeeld wordt een puntkomma (;) als scheidingsteken gebruikt. Gebruik voor andere platforms dan Microsoft Windows een dubbele punt (:) als scheidingsteken.

Het hulpprogramma geeft het gecodeerde wachtwoord uit, dat u naar het [!DNL .properties] bestand moet kopiëren.
