---
description: 'null'
seo-description: 'null'
seo-title: Videoanalysemogelijkheden initialiseren en configureren
title: Videoanalysemogelijkheden initialiseren en configureren
uuid: c49c77d9-66b9-4586-9d70-b139b4a97a7a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

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
   <td colname="col1"> <span class="filepath"> ADBMobileConfig.json </span> </td> 
   <td colname="col2"> <p>Belangrijk:  Dit JSON-configuratiebestand moet ADBMobileConfig.json blijven <span class="filepath"> </span>. De naam en het pad van dit configuratiebestand kunnen niet worden gewijzigd. Het pad naar dit bestand moet <span class="filepath"> &lt;source root&gt;/assets zijn </span>. </p> </td> 
  </tr> 
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
 </tbody> 
</table>

U kunt als volgt video bijhouden in uw speler configureren:

1. Controleer of de opties voor de laadtijd in het `ADBMobileConfig.json` bronbestand correct zijn.

       &quot;
     {
    &quot;version&quot;: &quot;1.1&quot;,
     &quot;analytics&quot;: {
 &quot;     sids&quot;: &quot;adobedevelopment&quot;,
     &quot;server&quot;: &quot;10.131.129.149:3000&quot;,
     &quot;charset&quot; : &quot;UTF-8&quot;,
     &quot;ssl&quot;: false,
     &quot;offlineEnabled&quot; : false,
     &quot;lifecycleTimeout&quot;: 5,
     &quot;batchLimit&quot;: 50,
     &quot;privacyDefault&quot; : &quot;optedin&quot;,
     &quot;poi&quot;: []
     },
     &quot;marketingCloud&quot;: {
 &quot;org&quot;     : &quot;ADOBE PROVIDED VALUE&quot;
     },
 &quot;     target&quot;: {
     &quot;clientCode&quot;: &quot;&quot;,
     &quot;timeout&quot;: 5
     },
     &quot;publiekManager&quot;: {
     &quot;server&quot;: &quot;&quot;
     }
     
     &quot;
     
     Dit JSON-configuratiebestand wordt gebundeld als een bron met TVSDK. De speler leest deze waarden alleen tijdens het laden en de waarden blijven constant tijdens de uitvoering van de toepassing.
       
     Voor het configureren van opties voor de laadtijd:
   
   1. Controleer of het `ADBMobileConfig.json` bestand de juiste waarden bevat (opgegeven door Adobe).
   1. Bevestig dat dit bestand zich in de `assets/` map bevindt.

      Deze map moet zich in de hoofdmap van de bronstructuur van de toepassing bevinden.

   1. Compileer en bouw uw toepassing.
   1. Implementeer en voer de gebundelde toepassing uit.

      Zie Video [meten in Adobe Analytics](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/video/)voor meer informatie over deze instellingen voor AppMeasurement.

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

   1. Stel de metagegevens voor Video-analyse in op de `videoAnalyticsProvider` instantie.

      ```java
      videoAnalyticsProvider.setVideoAnalyticsMetadata(vaMetadata);
      ```

   1. Koppel de instantie van de mediaspeler aan de `videoAnalyticsProvider` instantie:

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
