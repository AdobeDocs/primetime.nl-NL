---
description: De Primetime-speler ondersteunt de integratie van Primetime DRM als aangepaste DRM-workflows. Dit betekent dat uw toepassing de DRM-verificatieworkflows moet implementeren voordat de stream kan worden afgespeeld.
title: DRM-inhoudsbeveiliging
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---


# DRM-inhoudsbeveiliging {#drm-content-protection}

De Primetime-speler ondersteunt de integratie van Primetime DRM als aangepaste DRM-workflows. Dit betekent dat uw toepassing de DRM-verificatieworkflows moet implementeren voordat de stream kan worden afgespeeld.

Om dit in te schakelen, biedt TVSDK u de DRM-manager voor verificatie. De voorbeeldimplementatie biedt een voorbeeld van de volgende workflows:

* Hoe te om HLS stromen met de inhoudsbescherming van de Toegang te laden en terug te spelen, die voor lage foutenpercentages en snelle opstart wordt geoptimaliseerd.
* Hoe te om HLS stromen met AES128 inhoudsbescherming te laden en terug te spelen.
* HLS-streams laden en afspelen met PHLS-inhoudsbeveiliging, geoptimaliseerd voor lage foutsnelheden en snel opstarten.

Alle met DRM beveiligde inhoud wordt automatisch verwerkt door de DRM-bibliotheken die in de TVSDK zijn ingebouwd. U kunt echter foutafhandeling, optimalisatie van apparaatindividualisatie en licentieverwerving beschikbaar maken met TVSDK API-callbacks.

## Inhoud beschermen aan speler {#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

U kunt inhoudsbeveiliging toevoegen aan de speler door een afspeelbeheer te maken of door de beheerfactory te gebruiken.

Een contentbeveiligingsmanager maken:

* Initialiseer het DRM-systeem.

   Het volgende codevoorbeeld toont het roepen `loadDRMServices` in de toepassing `onCreate()` functie, om ervoor te zorgen dat om het even welke initialisering die voor het DRM systeem wordt vereist alvorens playback in werking wordt gesteld begint.

   ```java
   @Override 
    public void onCreate() { 
        super.onCreate();  
        DrmManager.loadDRMServices(getApplicationContext()); 
    }
   ```

* Laad de DRM-licenties vooraf.

   In het volgende codevoorbeeld wordt het laden van de `VideoItems` getoond wanneer de inhoudslijst klaar is met laden. Hierdoor worden de DRM-licenties opgehaald van de licentieserver en lokaal in het cachegeheugen opgeslagen, zodat de inhoud zo snel mogelijk wordt geladen wanneer het afspelen wordt gestart.

   ```java
   DrmManager.preLoadDrmLicenses(item.getUrl(),  
     new MediaPlayerItemLoader.LoaderListener() { 
   
       @Override 
       public void onLoadComplete(MediaPlayerItem item) { 
           Player.logger.w(LOG_TAG + "::DRMPreload#onLoadComplete", item.getResource().getUrl()); 
       } 
   
       @Override 
       public void onError(MediaErrorCode errorCode, String s) { 
           Player.logger.e(LOG_TAG + "::DRMPreload#onError", s); 
       } 
   } 
   ```

   >[!NOTE]
   >
   >U kunt Prekache DRM-licenties instellen op ON in de gebruikersinterface Instellingen om DRM-licenties te controleren bij het laden van inhoud. Het wordt echter aanbevolen een bepaald item vooraf te laden in plaats van alle licenties in de catalogus vooraf te laden.
   >
   >![](assets/precache-drm-licenses.jpg)

* Als u `ManagerFactory` wilt gebruiken om DRM-foutafhandeling te implementeren, moet u ervoor zorgen dat de volgende coderegel in het [!DNL PlayerFragment.java]-bestand staat:

   ```java
   drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
   ```

**Gerelateerde API-documentatie**

* [Class DRmManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DRmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)