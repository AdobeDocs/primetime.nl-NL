---
description: De Flash Runtime TVSDK heeft een ondertekend token nodig om te controleren of u het recht hebt om de TVSDK API aan te roepen in het domein waar uw toepassing zich bevindt.
seo-description: De Flash Runtime TVSDK heeft een ondertekend token nodig om te controleren of u het recht hebt om de TVSDK API aan te roepen in het domein waar uw toepassing zich bevindt.
seo-title: Uw ondertekende token laden
title: Uw ondertekende token laden
uuid: 8760eab3-3d6d-47c6-9aa7-f64f6aa5ddcf
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Uw ondertekende token {#load-your-signed-token} laden

De Flash Runtime TVSDK heeft een ondertekend token nodig om te controleren of u het recht hebt om de TVSDK API aan te roepen in het domein waar uw toepassing zich bevindt.

1. Krijg een ondertekend teken van uw Adobe vertegenwoordiger voor elk van uw domeinen (waar elk domein een specifiek domein of een vervangingsdomein zou kunnen zijn).

       Als u een token wilt ophalen, verschaft u Adobe het domein waarin de toepassing wordt opgeslagen of geladen, of bij voorkeur het domein als een SHA256-hash. Als tegenprestatie biedt Adobe u een getekende token voor elk domein. Deze tokens hebben een van de volgende vormen:
   
   * Een [!DNL .xml]-bestand dat fungeert als token voor één domein of jokertekendomein.

      >[!NOTE]
      >
      >Een token voor een jokertekendomein dekt dat domein en alle subdomeinen ervan. Een jokertekentoken voor het domein [!DNL mycompany.com] dekt bijvoorbeeld ook [!DNL vids.mycompany.com] en [!DNL private.vids.mycompany.com]; een jokerteken voor [!DNL vids.mycompany.com] zou ook [!DNL private.vids.mycompany.com] dekken. *Jokerdomeintokens worden alleen ondersteund voor bepaalde Flash Player-versies.*

   * Een [!DNL .swf]-bestand met tokeninformatie voor meerdere domeinen (exclusief jokertekens) (enkelvoudig of jokerteken) die uw toepassing dynamisch kan laden.

1. Sla het tokenbestand op dezelfde locatie of hetzelfde domein als de toepassing op.

   Standaard zoekt TVSDK naar het token op deze locatie. U kunt ook de naam en locatie van het token opgeven in `flash_vars` in het HTML-bestand.
1. Als uw tokenbestand één XML-bestand is:
   1. Gebruik `utils.AuthorizedFeaturesHelper.loadFrom` om de gegevens te downloaden die bij gespecificeerde URL (het symbolische dossier) worden opgeslagen en `authorizedFeatures` informatie uit het te halen.

      Deze stap kan variëren. U kunt bijvoorbeeld de verificatie uitvoeren voordat u de toepassing start, of u kunt de token rechtstreeks ontvangen van uw inhoudsbeheersysteem (CMS).

   1. TVSDK verzendt een `COMPLETED`-gebeurtenis als het laden is geslaagd of een `FAILED`-gebeurtenis anders. Voer de juiste actie uit wanneer u een van beide gebeurtenissen detecteert.

      Uw toepassing kan de vereiste `authorizedFeatures`-objecten alleen in de vorm van een `MediaPlayerContext` aan TVSDK leveren.
   In dit voorbeeld wordt getoond hoe u een single-token [!DNL .xml]-bestand kunt gebruiken.

   ```
   private function loadDirectTokenURL():void { 
       var url:String = constructAuthorizedFeatureTokenURL(); 
       _logger.debug("#onApplicationComplete Loading token from [{0}].", url); 
       _authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       _authorizedFeatureHelper.addEventListener(Event.COMPLETE,  
           onFeatureComplete); 
       _authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR,  
           onFeatureError); 
        _authorizedFeatureHelper.loadFrom(url); 
    }
   ```

1. Als uw token een [!DNL .swf]-bestand is:
   1. Definieer een `Loader`-klasse om het [!DNL .swf]-bestand dynamisch te laden.
   1. Stel de `LoaderContext` in om de laden op te geven die in het huidige toepassingsdomein moet worden uitgevoerd, zodat TVSDK het juiste token kan kiezen in het bestand [!DNL .swf]. Als `LoaderContext` niet wordt gespecificeerd, is de standaardactie van `Loader.load` .swf in het kinddomein van het huidige domein te laden.
   1. Luister naar de COMPLETE-gebeurtenis, die door TVSDK wordt verzonden als het laden is gelukt.

      Luister ook naar de gebeurtenis ERROR en voer de juiste actie uit.
   1. Als het laden is gelukt, gebruikt u `AuthorizedFeaturesHelper` om een `ByteArray` te verkrijgen dat de met PCKS-7 gecodeerde beveiligingsgegevens bevat.

      Deze gegevens worden via de AVE V11-API gebruikt om verificatie van de Flash Runtime Player te verkrijgen. Als de bytearray geen inhoud bevat, gebruikt u in plaats daarvan de procedure om te zoeken naar een token-bestand voor één domein.
   1. Gebruik `AuthorizedFeatureHelper.loadFeatureFromData` om de vereiste gegevens op te halen uit de bytearray.
   1. Verwijder het [!DNL .swf]-bestand.

   In de volgende voorbeelden ziet u hoe u een bestand met meerdere token [!DNL .swf] kunt gebruiken.

   **Voorbeeld 1 van meerdere token:**

   ```
   private function onApplicationComplete(event:FlexEvent):void { 
       var url:String = constructAuthorizedFeatureTokenURLFromSwf();   
       _loader = new Loader(); 
       var swfUrl:URLRequest = new URLRequest(url); 
       var loaderContext:LoaderContext =  
           new LoaderContext(false, ApplicationDomain.currentDomain, null); 
       _loader.contentLoaderInfo.addEventListener(Event.COMPLETE,  
           modEventHandler); 
       _loader.contentLoaderInfo.addEventListener(IOErrorEvent.IO_ERROR,  
           errEventHandler); 
       _loader.contentLoaderInfo.addEventListener(ProgressEvent.PROGRESS,  
           onProgressHandler); 
       _loader.uncaughtErrorEvents.addEventListener(UncaughtErrorEvent. 
           UNCAUGHT_ERROR, uncaughtEventHandler); 
       _logger.debug("# Loading token swf with context from [{0}].", url); 
       _loader.load(swfUrl, loaderContext); 
   } 
   
   private function modEventHandler(e:Event):void { 
       _logger.debug("loadSWF with domainID {0}",  
       SecurityDomain.currentDomain.domainID); 
       var loader : Loader = e.currentTarget.loader as Loader; 
       var myAuthorizedTokensLoaderClass:Class =  
           loader.contentLoaderInfo.applicationDomain. 
           getDefinition("AuthorizedTokensLoader") as Class; 
       var myTokens:Object = new myAuthorizedTokensLoaderClass(); 
       _authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       _authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       _authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       var byteArray:ByteArray = myTokens. 
           FetchToken(SecurityDomain.currentDomain.domainID); 
       if (myTokens == null || byteArray == null || byteArray.length == 0) 
           loadDirectTokenURL(); 
       else { 
           _logger.debug("token bytearry size {0}", byteArray.length); 
           _authorizedFeatureHelper.loadFeatureFromData(byteArray); 
       } 
       _loader.unload(); 
   } 
   ```

   **Voorbeeld 2 van meerdere token:**

   ```
   private function tokenSwfLoadedHandler(e:Event):void { 
       trace("loadSWF with domainID {0}", SecurityDomain.currentDomain.domainID); 
       var loader : Loader = e.currentTarget.loader as Loader; 
       var myAuthorizedTokensLoaderClass:Class =  
         loader.contentLoaderInfo.applicationDomain. 
         getDefinition("AuthorizedTokensLoader") as Class; 
       var myTokens:Object = new myAuthorizedTokensLoaderClass(); 
       authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       var byteArray:ByteArray =  
           myTokens.FetchToken(SecurityDomain.currentDomain.domainID); 
       var myDomains:Array = ["domain.com"]; 
       if (byteArray == null || byteArray.length == 0) { 
           // check for wildcard tokens 
           if (myTokens.hasOwnProperty("FetchWildCardToken") == true) { 
               // contains wildcard domains 
               for each (var domain:String in myDomains) { 
                   byteArray = myTokens.FetchWildCardToken(domain); 
                   if (byteArray != null && byteArray.length != 0) { 
                       break; 
                   } 
               }; 
           } 
       } 
   
       if (myTokens == null || byteArray == null || byteArray.length == 0) 
           loadDirectTokenURL(); 
       else { 
           trace("token bytearry size {0}", byteArray.length); 
           authorizedFeatureHelper.loadFeatureFromData(byteArray); 
       } 
       _loader.unload(); 
   } 
   
   private function loadDirectTokenURL():void { 
       trace("#onApplicationComplete Loading token from [{0}].", tokenUrl); 
       authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       authorizedFeatureHelper.loadFrom(tokenUrl); 
   }
   ```

