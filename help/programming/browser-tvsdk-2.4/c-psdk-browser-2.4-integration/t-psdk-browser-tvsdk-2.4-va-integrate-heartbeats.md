---
description: U kunt de speler configureren om het videogebruik te volgen en te analyseren.
seo-description: U kunt de speler configureren om het videogebruik te volgen en te analyseren.
seo-title: Videoanalysemogelijkheden initialiseren en configureren
title: Videoanalysemogelijkheden initialiseren en configureren
uuid: 4a582b35-ae92-4557-806d-e174fc878cc5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---


# Videoanalysemogelijkheden initialiseren en configureren {#initialize-and-configure-video-analytics}

U kunt de speler configureren om het videogebruik te volgen en te analyseren.

Controleer of u het volgende hebt voordat u video-tracking (videohartslagen) activeert:

* Configuratie/Browser TVSDK Initialisatiegegevens - Neem contact op met uw Adobe-vertegenwoordiger voor uw specifieke informatie over uw video-tracking-account:

<table id="table_3565328ABBEE4605A92EAE1ADE5D6F84">
 <tbody>
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
   
   * Instantiatie vereist een Marketing Cloud organisatie-id-invoerparameter die door Adobe wordt opgegeven.

      Dit is een tekenreekswaarde.
   * De enige configuratieoptie voor de bibliotheek VisitorAPI is URL van het achterste eindpunt dat unieke herkenningsteken voor de huidige gebruiker verstrekt.
   * De URL van de server voor het bijhouden van bezoekers is gelijk aan de URL van de analytische trackingserver.

      Voor informatie over het uitvoeren van de Dienst van identiteitskaart van de Bezoeker, zie [Implementatie van de Dienst van identiteitskaart van de Bezoeker](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-target.html).

   ```js
   var_visitor = new Visitor("MARKETING_CLOUD_ORG_ID");
   _visitor.trackingServer = "URL_OF_THE_VISITOR_TRACKER_SERVER”;
   ```

2. Instantieer en vorm de component AppMeasurement.

   De instantie AppMeasurement heeft vele configuratieopties. Raadpleeg de documentatie van [Adobe Analytics Developer](https://microsite.omniture.com/t2/help/en_US/reference/#Developer) voor meer informatie. De opties in de volgende voorbeeldcode ( `account`, `visitorNamespace`, en `trackingServer`) worden vereist, en de waarden worden verstrekt door Adobe.

   >[!IMPORTANT]
   >
   >U moet ervoor zorgen dat de afhankelijkheidsketen correct is ingesteld. De instantie AppMeasurement aggregeert (afhankelijk van) de API-component van de bezoeker.

   ```js
   var appMeasurement = new AppMeasurement();
   appMeasurement.visitor = visitor;
   appMeasurement.trackingServer = 'URL_OF_THE_ADOBE_ANALYTICS_TRACKING_SERVER';
   appMeasurement.account = 'ACCOUNT_NAME'; // Also known as RSID
   appMeasurement.pageName = 'Sample Page Name';
   appMeasurement.charSet = "UTF-8";
   appMeasurement.visitorID = "test-vid";
   ```

   >[!IMPORTANT]
   >
   >Controleer in uw toepassing of `appMeasurementObject.visitor` is gevuld voordat u de videovertaling start, of dat er geen resultaten bij het bijhouden van de video worden weergegeven. Deze resultaten worden vermeld door de berichten in uw logboek. U kunt een lege spoorvraag ( `appMeasurementObject.track`) toevoegen, het `visitor` bezit onderzoeken tot het wordt bevolkt, en videoanalyses in werking stellen.

3. Metagegevens voor het bijhouden van videokaarten initialiseren en configureren.

   >[!IMPORTANT]
   >
   >U kunt de module voor videoanalyse halverwege de stream stoppen en indien nodig opnieuw initialiseren. Voordat de module opnieuw wordt geïnitialiseerd, moet u ervoor zorgen dat de metagegevens voor videoanalyse ook worden bijgewerkt naar de juiste metagegevens voor de inhoud. Herhaal substappen 1 en 2 om de metagegevens opnieuw te maken.

   1. Maak een instantie van de metagegevens voor videoanalyse.
Deze instantie bevat alle configuratiegegevens die nodig zijn om het bijhouden van videogarakters in te schakelen. Bijvoorbeeld:

      ```js
      function getVideoAnalyticsMetadata() {
          var vaObj = new AdobePSDK.VA.VideoAnalyticsMetadata();
          vaObj.appMeasurement = appMeasurement;
          vaObj.trackingServer = 'hbTrackingServer';
          vaObj.publisher = 'hbPublisher';
          vaObj.channel = 'sample-channel';
          vaObj.playerName = 'TVSDK-HTML';
          vaObj.appVersion = '1.0.0';
          vaObj.videoName = 'hbFriendlyName'; // this will overwrite the ContextData variable a.media.friendlyName
          vaObj.assetDuration = durationInSeconds;
          // use this to override the default asset length of -1 for live streams
          vaObj.debugLogging = false;
          return vaObj;
      }
      ```

   2. Nadat u een mediaspeler-instantie hebt gemaakt, maakt u een tracker voor Video Analytics en geeft u een verwijzing naar de mediaafspeelinstantie.
Houd rekening met het volgende:

      * Maak altijd een nieuwe tracker-instantie voor elke afspeelsessie van de inhoud en verwijder de vorige referentie (na het loskoppelen van de instantie van de mediaspeler).
      * De metagegevens die in substap 1 zijn gemaakt, moeten worden opgegeven in de constructor of Video Analytics Tracker.

         ```js
         var videoAnalyticsMetadata = getVideoAnalyticsMetadata();
         videoAnalyticsProvider = new AdobePSDK.VA.VideoAnalyticsProvider(videoAnalyticsMetadata);
         videoAnalyticsProvider.attachMediaPlayer(player);
         ```
   3. Vernietig de videoanalysetracker.
Voordat u een nieuwe afspeelsessie voor inhoud begint, moet u de vorige instantie van de videotracering vernietigen. Nadat u de gebeurtenis &#39;complete&#39; van de inhoud (of het bericht) hebt ontvangen, wacht u een paar minuten voordat u de instantie van de videotracker vernietigt. Het vernietigen van de instantie onmiddellijk zou kunnen interfereren met de capaciteit van de Videoanalysator om een video te verzenden volledig pingelt.

      ```js
      if (videoAnalyticsProvider) {
          videoAnalyticsProvider.detachMediaPlayer();
          videoAnalyticsProvider = null;
      ```
   4. Markeer de live/lineaire stream handmatig als voltooid.
Als u verschillende afleveringen hebt op één live stream, kunt u een aflevering handmatig als voltooid markeren met de volledige API. Hiermee beëindigt u de sessie voor het bijhouden van de video voor de huidige video-uitzending en kunt u een nieuwe traceringssessie starten voor de volgende uitzending.
      >[!TIP]
      >
      >Deze API is optioneel en is niet nodig voor het bijhouden van VOD-video.

      ```js
      if (videoAnalyticsProvider)
      {
         videoAnalyticsProvider.trackVideoComplete();
      videoAnalyticsProvider.detachMediaPlayer();
      videoAnalyticsProvider = null;
      // Create a new instance of VideoAnalyticsProvider to continue tracking.
      } 
      ```
