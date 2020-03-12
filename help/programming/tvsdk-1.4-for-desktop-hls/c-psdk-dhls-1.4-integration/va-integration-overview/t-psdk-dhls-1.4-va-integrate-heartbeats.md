---
description: U kunt de speler configureren om het videogebruik te volgen en te analyseren.
seo-description: U kunt de speler configureren om het videogebruik te volgen en te analyseren.
seo-title: Videoanalysemogelijkheden initialiseren en configureren
title: Videoanalysemogelijkheden initialiseren en configureren
uuid: ece5ddc1-3f7b-4878-b1bc-1fec0a459add
translation-type: tm+mt
source-git-commit: 6cb3463be8986d8a1dc718655bd929a0f07ac00d

---


# Videoanalysemogelijkheden initialiseren en configureren{#initialize-and-configure-video-analytics}

U kunt de speler configureren om het videogebruik te volgen en te analyseren.

Controleer of u het volgende hebt voordat u video-tracking (videohartslagen) activeert:

* TVSDK voor desktop HLS
* Configuratie-/initialisatiegegevens - Neem contact op met uw Adobe-vertegenwoordiger voor uw specifieke informatie over uw account voor het bijhouden van video&#39;s:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> Het eindpunt van de toepassingsmeetserver </td> 
   <td colname="col2"> De URL van het achterste eindpunt van de Adobe Analytics-verzameling (voorheen SiteCatalyst). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Het servereindpunt voor videoanalyse bijhouden </td> 
   <td colname="col2"> De URL van het back-end verzameleindpunt van de videoanalyse. Dit is waar alle video hartslag het volgen vraag wordt verzonden. <p>Tip:  De URL van de server voor het bijhouden van bezoekers is gelijk aan de URL van de analytische trackingserver. Voor informatie over het uitvoeren van de Dienst van identiteitskaart van de Bezoeker, zie de Dienst van identiteitskaart van het <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external"> Uitvoeren </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Accountnaam </td> 
   <td colname="col2"> Ook gekend als identiteitskaart van de Reeks van het Rapport (RSID). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Organisatie-id van Marketing Cloud </td> 
   <td colname="col2"> Een tekenreekswaarde die is vereist voor het instantiëren van de component Visitor. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Het servereindpunt van de Bezoeker </td> 
   <td colname="col2"> URL van het achterste eindpunt dat een unieke herkenningsteken voor de huidige videokijker verstrekt. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uitgever </td> 
   <td colname="col2"> Dit is de uitgevers-id die door hun Adobe-vertegenwoordiger aan klanten wordt geleverd. <p>Tip:  Deze id is niet alleen een tekenreeks met de naam merk/televisie. </p> </td> 
  </tr> 
 </tbody> 
</table>

U kunt als volgt video bijhouden in uw speler configureren:

1. Instantiëren en configureren van de VisitorAPI-bibliotheek.

       Houd rekening met het volgende:
   
   * Voor Instantiatie is een door Adobe opgegeven invoerparameter voor de organisatie-id van de Marketing Cloud vereist.

      Dit is een tekenreekswaarde.
   * De enige configuratieoptie voor de bibliotheek VisitorAPI is URL van het achterste eindpunt dat unieke herkenningsteken voor de huidige gebruiker verstrekt.
   * De URL van de server voor het bijhouden van bezoekers is gelijk aan de URL van de analytische trackingserver.

      Voor informatie over het uitvoeren van de Dienst van identiteitskaart van de Bezoeker, zie de Implementatie van de Dienst van identiteitskaart van de Bezoeker

   ```
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID"); 
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”; 
   ```

1. Instantieer en vorm de component AppMeasurement.

   De instantie AppMeasurement heeft vele configuratieopties. Raadpleeg de documentatie van [Adobe Analytics Developer](https://microsite.omniture.com/t2/help/en_US/reference/#Developer) voor meer informatie. De opties in de volgende voorbeeldcode ( `account`, `visitorNamespace`, en `trackingServer`) zijn vereist, en de waarden worden verstrekt door Adobe.

   >[!IMPORTANT]
   >
   >U moet ervoor zorgen dat de afhankelijkheidsketen correct is ingesteld. De instantie AppMeasurement aggregeert (afhankelijk van) de API-component van de bezoeker.

   ```
   // Instantiate and configure AppMeasurement 
   
   // Instantiate AppMeasurement instance only once! 
   if (_appMeasurementObject == null) {  
       _appMeasurementObject = new AppMeasurement(); 
   } 
   
   with (_appMeasurementObject) { 
       account = "ACCOUNT_NAME"; // Also known as RSID 
       trackingServer = "URL_OF_THE_ADOBE_ANALYTICS_TRACKING_SERVER"; 
   
       // Use the same value here as for the Visitor API component 
       visitorNamespace = "MARKETING_CLOUD_ORG_ID"; 
   
       // Attach the Visitor API to the AppMeasurement instance. 
       visitor = _visitor;  
       pageName = "pageName"; 
       charSet = "UTF-8"; 
       currencyCode = "USD"; 
   } 
   ```

   >[!IMPORTANT]
   >
   >Zorg ervoor dat de video in uw toepassing `appMeasurementObject.visitor` is gevuld voordat u de stroom voor videoanalyse start, of u krijgt geen resultaten voor het bijhouden van de video. Deze resultaten worden vermeld door de berichten in uw logboek. U kunt een lege spoorvraag ( `appMeasurementObject.track`) toevoegen, het `visitor` bezit onderzoeken tot het wordt bevolkt, en videoanalyses in werking stellen.

1. Metagegevens voor het bijhouden van videokaarten initialiseren en configureren.

   >[!IMPORTANT]
   >
   >U kunt de module voor videoanalyse halverwege de stream stoppen en indien nodig opnieuw initialiseren. Voordat de module opnieuw wordt geïnitialiseerd, moet u ervoor zorgen dat de metagegevens voor videoanalyse ook worden bijgewerkt naar de juiste metagegevens voor de inhoud. Herhaal substappen 1 en 2 om de metagegevens opnieuw te maken.

   1. Maak een instantie van de metagegevens voor videoanalyse.

      Deze instantie bevat alle configuratiegegevens die nodig zijn om het bijhouden van videogarakters in te schakelen. Bijvoorbeeld:

      ```
      private function getVideoAnalyticsTrackingMetadata():VideoAnalyticsMetadata {     
          // Initialize visitor id service and appMeasurement      
          [...] // as shown in the previous steps     
      
          var vaMetadata:VideoAnalyticsMetadata = new VideoAnalyticsMetadata(); 
      
          with (vaMetadata) { 
              trackingServer = "hbTrackingServer"; 
              publisher = "hbPublisher"; 
              channel = "hbChannel";  
              playerName = "hbPlayerName"; 
      
              // this overwrites the ContextData variable a.media.friendlyName 
              videoName = "hbFriendlyName";  
      
              // this will overwrite the ContextData variable a.media.name 
              videoId = "hbName"; 
      
              enableChapterTracking = true; 
      
              // Set these to false for production deployment 
              debugLogging = true;  
              quietMode = false; 
      
          } 
      } 
      ```

   1. Voeg de metagegevens voor videoanalyse toe aan de algemene metagegevensinstantie.

      Wanneer u klaar bent, stelt u de algemene metagegevensinstantie in op de mediabron of het item voor de mediaspeler:

      ```
      var resourceMetadata:Metadata = _player.currentItem.resource.metadata; 
      resourceMetadata.setMetadata(DefaultMetadataKeys.VIDEO_ANALYTICS_METADATA_KEY,  
                                   getVideoAnalyticsTrackingMetadata());
      ```

   1. Initialiseer de videoanalysator.

      Nadat u een mediaspeler-instantie hebt gemaakt, moet u een tracker-instantie Video Analytics maken en een verwijzing naar de mediaspeler-instantie opgeven.

      >[!TIP]
      >
      >Maak altijd een nieuwe tracker-instantie voor elke afspeelsessie van de inhoud en verwijder de vorige verwijzing nadat u de instantie van de mediaspeler hebt losgekoppeld.

      ```
      _videoAnalyticsProvider = new VideoAnalyticsProvider(_appMeasurementObject); 
      _videoAnalyticsProvider.attachMediaPlayer(_player);
      ```

   1. Vernietig de videoanalysetracker.

      Voordat u een nieuwe afspeelsessie voor inhoud begint, moet u de vorige instantie van de videotracering vernietigen. Nadat u de gebeurtenis &#39;complete&#39; van de inhoud (of het bericht) hebt ontvangen, wacht u een paar minuten voordat u de instantie van de videotracker vernietigt. Het vernietigen van de instantie onmiddellijk zou kunnen interfereren met de capaciteit van de Videoanalysator om een video te verzenden volledig pingelt.

      ```
      if (videoAnalyticsTracker) { 
          videoAnalyticsTracker.detachMediaPlayer(); 
          videoAnalyticsTracker = null; 
      }
      ```

   1. Markeer de live/lineaire stream handmatig als voltooid.

      Als u verschillende afleveringen hebt op één live stream, kunt u een aflevering handmatig als voltooid markeren met de volledige API. Hiermee beëindigt u de sessie voor het bijhouden van de video voor de huidige video-uitzending en kunt u een nieuwe traceringssessie starten voor de volgende uitzending.

      >[!TIP]
      >
      >Deze API is optioneel en is niet nodig voor het bijhouden van VOD-video.

