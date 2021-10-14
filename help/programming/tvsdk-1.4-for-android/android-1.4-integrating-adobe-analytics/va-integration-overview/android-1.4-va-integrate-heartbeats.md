---
description: U kunt de speler configureren om het videogebruik te volgen en te analyseren.
title: Videoanalysemogelijkheden initialiseren en configureren
exl-id: 82013882-e314-44fd-82f2-0640575d3c68
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Videoanalysemogelijkheden initialiseren en configureren{#initialize-and-configure-video-analytics}

U kunt de speler configureren om het videogebruik te volgen en te analyseren.

Controleer of u het volgende hebt voordat u video-tracking (videohartslagen) activeert:

* TVSDK voor Android
* Configuratie-/initialisatiegegevens - Neem contact op met uw Adobe-vertegenwoordiger voor uw specifieke accountgegevens voor het bijhouden van video:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>Belangrijk:  Dit JSON-configuratiebestand moet <span class="codeph"> ADBMobileConfig.json </span> blijven. De naam en het pad van dit configuratiebestand kunnen niet worden gewijzigd. Het pad naar dit bestand moet <span class="codeph"> &lt;source root&gt;/assets </span> zijn. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Het eindpunt van de trackingserver voor AppMeturement </td> 
   <td colname="col2"> De URL van het achterste eindpunt van de Adobe Analytics-verzameling (voorheen SiteCatalyst). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Het servereindpunt voor videoanalyse bijhouden </td> 
   <td colname="col2"> De URL van het back-end verzameleindpunt van de videoanalyse. Dit is waar alle video hartslag het volgen vraag wordt verzonden. <p>Tip:  De URL van de server voor het bijhouden van bezoekers is gelijk aan de URL van de analytische trackingserver. Voor informatie over het uitvoeren van de Dienst van identiteitskaart van de Bezoeker, zie <a href="https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-target.html?lang=en" format="html" scope="external"> de Dienst </a> van identiteitskaart uitvoeren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Accountnaam </td> 
   <td colname="col2"> Ook gekend als identiteitskaart van de Reeks van het Rapport (RSID). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Organisatie-id Marketing Cloud </td> 
   <td colname="col2"> Een tekenreekswaarde die is vereist voor het instantiëren van de component Visitor. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Uitgever </td> 
   <td colname="col2"> Dit is de uitgevers-id die door hun Adobe-vertegenwoordiger aan klanten wordt geleverd. <p>Tip:  Deze id is niet alleen een tekenreeks met de naam merk/televisie. </p> </td> 
  </tr> 
 </tbody> 
</table>

U kunt als volgt video bijhouden in uw speler configureren:

1. Bevestig dat de lading-tijd opties in het `ADBMobileConfig.json` middeldossier correct zijn.

   ```
   { 
       "version" : "1.1", 
       "analytics" : { 
           "rsids" : "adobedevelopment", 
           "server" : "10.131.129.149:3000", 
           "charset" : "UTF-8", 
           "ssl" : false, 
           "offlineEnabled" : false, 
           "lifecycleTimeout" : 5, 
           "batchLimit" : 50, 
           "privacyDefault" : "optedin", 
           "poi" : [] 
       }, 
       "marketingCloud": { 
           "org": "ADOBE PROVIDED VALUE"  
       }, 
       "target" : { 
           "clientCode" : "", 
           "timeout" : 5 
       }, 
       "audienceManager" : { 
           "server" : "" 
       } 
   }
   ```

   Dit JSON-configuratiebestand wordt gebundeld als bron met TVSDK. De speler leest deze waarden alleen tijdens het laden en de waarden blijven constant tijdens de uitvoering van de toepassing.

   Opties voor laadtijd configureren:

   1. Bevestig dat het `ADBMobileConfig.json`-bestand de juiste waarden bevat die door Adobe worden opgegeven.
   1. Bevestig dat dit bestand zich in de map `assets` bevindt.

      Deze map moet zich in de hoofdmap van de bronstructuur van de toepassing bevinden.
   1. Compileer en bouw uw toepassing.
   1. Implementeer en voer de gebundelde toepassing uit.

      Voor meer informatie over deze montages AppMeasurement, zie [Metende Video in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=en).
1. Metagegevens voor het bijhouden van videokaarten initialiseren en configureren.

   >[!IMPORTANT]
   >
   >U kunt de module voor videoanalyse halverwege de stream stoppen en indien nodig opnieuw initialiseren. Voordat de module opnieuw wordt geïnitialiseerd, moet u ervoor zorgen dat de metagegevens voor videoanalyse ook worden bijgewerkt naar de juiste metagegevens voor de inhoud. Herhaal substappen 1 en 2 om de metagegevens opnieuw te maken.

   1. Maak een instantie van de metagegevens voor videoanalyse.

      Deze instantie bevat alle configuratiegegevens die nodig zijn om het bijhouden van videogarakters in te schakelen. Bijvoorbeeld:

      ```java
      private VideoAnalyticsMetadata getVideoAnalyticsTrackingMetadata() { 
          VideoAnalyticsMetadata vaMetadata = new VideoAnalyticsMetadata(); 
      
          vaMetadata.setTrackingServer("example.com"); 
          vaMetadata.setPublisher("sample-publisher"); 
          vaMetadata.setChannel("test-channel"); 
          vaMetadata.setVideoName("myvideo"); 
          vaMetadata.setVideoId("myvideoid"); 
          vaMetadata.setPlayerName("PSDK Player"); 
          vaMetadata.setUseSSL(false); 
          vaMetadata.debugLogging = true; // Set to NO for production deployment. 
          vaMetadata.quietMode = false; // Set to NO for production deployment. 
          vaMetadata.setEnableChapterTracking(true); 
          // use this API to override the default asset length -1 for live streams 
          vaMetadata.setAssetDuration(SAMPLE_ASSET_DURATION); 
      
          return vaMetadata; 
      }
      ```

   1. Voeg de metagegevens voor videoanalyse toe aan de algemene metagegevensinstantie.

      Wanneer u klaar bent, stelt u de algemene metagegevensinstantie in op de mediabron of het item voor de mediaspeler:

      ```java
      ((MetadataNode)resourceMetadata).setNode( 
            DefaultMetadataKeys.VIDEO_ANALYTICS_METADATA_KEY.getValue(), vaMetadata);
      ```

   1. Initialiseer de videoanalysator.

      Nadat u een mediaspeler-instantie hebt gemaakt, moet u een tracker-instantie Video Analytics maken en een verwijzing naar de mediaspeler-instantie opgeven.

      >[!TIP]
      >
      >Maak altijd een nieuwe tracker-instantie voor elke afspeelsessie van de inhoud en verwijder de vorige verwijzing nadat u de instantie van de mediaspeler hebt losgekoppeld.

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider =  
        new VideoAnalyticsProvider(appContext); 
      
      // Attach the TVSDK media player instance 
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. Vernietig de videoanalysetracker.

      Voordat u een nieuwe afspeelsessie voor inhoud begint, moet u de vorige instantie van de videotracering vernietigen. Nadat u de gebeurtenis &#39;complete&#39; van de inhoud (of het bericht) hebt ontvangen, wacht u een paar minuten voordat u de instantie van de videotracker vernietigt. Het vernietigen van de instantie onmiddellijk zou kunnen interfereren met de capaciteit van de Videoanalysator om een video te verzenden volledig pingelt.

      ```java
      if (_videoAnalyticsProvider) { 
          _videoAnalyticsProvider.detachMediaPlayer(); 
          _videoAnalyticsProvider = null; 
      }
      ```

   1. Markeer de live/lineaire stream handmatig als voltooid.

      Als u verschillende afleveringen hebt op één live stream, kunt u een aflevering handmatig als voltooid markeren met de volledige API. Hiermee beëindigt u de sessie voor het bijhouden van de video voor de huidige video-uitzending en kunt u een nieuwe traceringssessie starten voor de volgende uitzending.

      >[!TIP]
      >
      >Deze API is optioneel en is niet nodig voor het bijhouden van VOD-video.

      ```java
      if (_videoAnalyticsProvider) { 
         _videoAnalyticsProvider.trackVideoComplete();    
      }
      ```
