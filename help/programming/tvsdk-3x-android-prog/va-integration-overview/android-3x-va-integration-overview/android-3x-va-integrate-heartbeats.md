---
title: Videoanalysemogelijkheden initialiseren en configureren
description: Videoanalysemogelijkheden initialiseren en configureren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---


# Videoanalysemogelijkheden initialiseren en configureren {#initialize-and-configure-video-analytics}

U kunt de speler configureren om het videogebruik te volgen en te analyseren.
Controleer of u het volgende hebt voordat u video-tracking (videohartslagen) activeert:

* TVSDK 3.0 voor Android.
* Configuratie-/initialisatiegegevens

   Neem contact op met uw Adobe-vertegenwoordiger voor uw specifieke accountgegevens voor het bijhouden van video:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json  </span> </td> 
   <td colname="col2"> <p>Belangrijk:  Dit JSON-configuratiebestand moet <span class="filepath"> ADBMobileConfig.json </span> blijven. De naam en het pad van dit configuratiebestand kunnen niet worden gewijzigd. Het pad naar dit bestand moet <span class="filepath"> &lt;source root&gt;/assets </span> zijn. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Het eindpunt van de trackingserver voor AppMeturement </td> 
   <td colname="col2"> De URL van het achterste eindpunt van de Adobe Analytics-verzameling (voorheen SiteCatalyst). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Het servereindpunt voor videoanalyse bijhouden </td> 
   <td colname="col2"> De URL van het back-end verzameleindpunt van de videoanalyse. Dit is waar alle video hartslag het volgen vraag wordt verzonden. <p>Tip:  De URL van de server voor het bijhouden van bezoekers is gelijk aan de URL van de analytische trackingserver. Voor informatie over het uitvoeren van de Dienst van identiteitskaart van de Bezoeker, zie <a href="https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html" format="html" scope="external"> de Dienst </a> van identiteitskaart uitvoeren. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Accountnaam </td> 
   <td colname="col2"> Ook gekend als identiteitskaart van de Reeks van het Rapport (RSID). </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Organisatie-id Marketing Cloud </td> 
   <td colname="col2"> Een tekenreekswaarde die is vereist voor het instantiëren van de component Visitor. </td> 
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


   1. Bevestig dat het `ADBMobileConfig.json`-bestand de juiste waarden bevat (opgegeven door Adobe).
   1. Bevestig dat dit bestand zich in de map `assets/` bevindt.

      Deze map moet zich in de hoofdmap van de bronstructuur van de toepassing bevinden.

   1. Compileer en bouw uw toepassing.
   1. Implementeer en voer de gebundelde toepassing uit.

      Voor meer informatie over deze montages AppMeasurement, zie [Metende Video in Adobe Analytics](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/).

1. Metagegevens voor het bijhouden van videokaarten initialiseren en configureren.

   >[!IMPORTANT]
   >
   >U kunt de module voor videoanalyse halverwege de stream stoppen en indien nodig opnieuw initialiseren. Voordat de module opnieuw wordt geïnitialiseerd, moet u ervoor zorgen dat de metagegevens voor videoanalyse ook worden bijgewerkt naar de juiste metagegevens voor de inhoud. Herhaal de eerste twee stappen hieronder (substappen **a** en **b**) om de metagegevens opnieuw te maken.

   1. Maak een instantie van de metagegevens voor videoanalyse.

      Deze instantie bevat alle configuratiegegevens die nodig zijn om het bijhouden van videogarakters in te schakelen. Bijvoorbeeld:

      ```java
      private VideoAnalyticsMetadata getVideoAnalyticsTrackingMetadata() { 
          VideoAnalyticsMetadata vaMetadata = new VideoAnalyticsMetadata(); 
      
          vaMetadata.setTrackingServer("example.com"); 
          vaMetadata.setChannel("test-channel"); 
          vaMetadata.setVideoName("myvideo"); 
          vaMetadata.setVideoId("myvideoid"); 
          vaMetadata.setPlayerName("PSDK Player"); 
          vaMetadata.setUseSSL(false); 
          vaMetadata.debugLogging = true; // Set to NO for production deployment. 
          vaMetadata.setEnableChapterTracking(true); 
          // use this API to override the default asset length -1 for live streams 
          vaMetadata.setAssetDuration(SAMPLE_ASSET_DURATION); 
      
          return vaMetadata; 
      }
      ```

   1. Initialiseer de provider Video Analytics.

      Nadat u een instantie van de mediaspeler hebt gemaakt, moet u een instantie van de provider Video Analytics maken en deze instantie de toepassingscontext geven.

      >[!TIP]
      >
      >Maak altijd een nieuwe providerinstantie voor elke afspeelsessie van de inhoud en verwijder de vorige verwijzing nadat u de instantie van de mediaspeler hebt losgekoppeld.

      ```java
      VideoAnalyticsProvider videoAnalyticsProvider = new VideoAnalyticsProvider(appContext); 
      ```

   1. Stel de metagegevens voor Video-analyse in op de instantie `videoAnalyticsProvider`.

      ```java
      videoAnalyticsProvider.setVideoAnalyticsMetadata(vaMetadata);
      ```

   1. Koppel de instantie van de mediaspeler aan de instantie `videoAnalyticsProvider`:

      ```java
      videoAnalyticsProvider.attachMediaPlayer(mediaPlayer); 
      ```

   1. Vernietig de provider Video Analytics.

      Voordat u met een nieuwe afspeelsessie begint, moet u het vorige exemplaar van de videoprovider vernietigen. Nadat u de gebeurtenis complete (of melding) voor de inhoud hebt ontvangen, wacht u een paar minuten voordat u de instantie van de videoanalyseprovider vernietigt. Het vernietigen van de instantie onmiddellijk zou kunnen interfereren met de leverancier van de Analyse Video om &quot;video volledig&quot;te verzenden pingelt.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.detachMediaPlayer(); 
          videoAnalyticsProvider = null; 
      }
      ```

   1. Markeer de live/lineaire stream handmatig als voltooid.

      Als u verschillende afleveringen hebt op één live stream, kunt u een aflevering handmatig als voltooid markeren met de volledige API. Hiermee beëindigt u de sessie voor het bijhouden van de video voor de huidige video-uitzending en kunt u een nieuwe traceringssessie starten voor de volgende uitzending.

      >[!TIP]
      >
      >Deze API is optioneel en werkt niet voor het bijhouden van VOD-video.

      ```java
      if (videoAnalyticsProvider) { 
          videoAnalyticsProvider.trackVideoComplete();    
      }
      ```
