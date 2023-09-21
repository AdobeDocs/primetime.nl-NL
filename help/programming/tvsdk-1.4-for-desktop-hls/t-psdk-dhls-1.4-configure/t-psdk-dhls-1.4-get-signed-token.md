---
description: De Flash Runtime TVSDK heeft een ondertekend token nodig om te controleren of u het recht hebt om de TVSDK API aan te roepen op het domein waar uw toepassing zich bevindt.
title: Uw ondertekende token laden
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Uw ondertekende token laden {#load-your-signed-token}

De Flash Runtime TVSDK heeft een ondertekend token nodig om te controleren of u het recht hebt om de TVSDK API aan te roepen op het domein waar uw toepassing zich bevindt.

1. Krijg een ondertekend teken van uw Adobe vertegenwoordiger voor elk van uw domeinen (waar elk domein een specifiek domein of een vervangingsdomein zou kunnen zijn).

       Als u een token wilt ophalen, verschaft u Adobe het domein waarin de toepassing wordt opgeslagen of geladen, of bij voorkeur het domein als een SHA256-hash. Als tegenprestatie biedt Adobe u een getekende token voor elk domein. Deze tokens hebben een van de volgende vormen:
   
   * An [!DNL .xml] bestand dat fungeert als token voor één domein of jokertekendomein.

     >[!NOTE]
     >
     >Een token voor een jokertekendomein dekt dat domein en alle subdomeinen ervan. Bijvoorbeeld een jokerteken voor het domein [!DNL mycompany.com] zou ook [!DNL vids.mycompany.com] en [!DNL private.vids.mycompany.com]; een jokerteken voor [!DNL vids.mycompany.com] zou ook [!DNL private.vids.mycompany.com]. *Jokerdomeintokens worden alleen ondersteund voor bepaalde versies van Flash Player.*

   * A [!DNL .swf] bestand met tokeninformatie voor meerdere domeinen (exclusief jokertekens) (enkelvoudig of jokerteken) die uw toepassing dynamisch kan laden.

1. Sla het tokenbestand op dezelfde locatie of hetzelfde domein als de toepassing op.

   Standaard zoekt TVSDK naar het token op deze locatie. U kunt ook de naam en locatie van het token opgeven in `flash_vars` in uw HTML-bestand.
1. Als uw tokenbestand één XML-bestand is:
   1. Gebruiken `utils.AuthorizedFeaturesHelper.loadFrom` om de gegevens te downloaden die zijn opgeslagen op de opgegeven URL (het tokenbestand) en het `authorizedFeatures` informatie van de Commissie.

      Deze stap kan variëren. U kunt bijvoorbeeld de verificatie uitvoeren voordat u de toepassing start, of u kunt de token rechtstreeks ontvangen van uw inhoudsbeheersysteem (CMS).

   1. TVSDK verzendt een `COMPLETED` als het laden is voltooid of als een `FAILED` anders. Voer de juiste actie uit wanneer u een van beide gebeurtenissen detecteert.

      Uw toepassing kan alleen de vereiste `authorizedFeatures` objecten voor TVSDK in de vorm van een `MediaPlayerContext`.

   In dit voorbeeld wordt getoond hoe u een token kunt gebruiken [!DNL .xml] bestand.

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

1. Als uw token een [!DNL .swf] bestand:
   1. Een `Loader` klasse om de [!DNL .swf] bestand.
   1. Stel de `LoaderContext` om het laden op te geven dat in het huidige toepassingsdomein moet worden uitgevoerd, zodat TVSDK het juiste token kan kiezen in het dialoogvenster [!DNL .swf] bestand. Indien `LoaderContext` is niet opgegeven, de standaardhandeling van `Loader.load` moet het SWF-bestand laden in het onderliggende domein van het huidige domein.
   1. Luister naar de COMPLETE-gebeurtenis, die door TVSDK wordt verzonden als het laden is gelukt.

      Luister ook naar de gebeurtenis ERROR en voer de juiste actie uit.
   1. Als het laden is gelukt, gebruikt u de `AuthorizedFeaturesHelper` om een `ByteArray` die de met PCKS-7 gecodeerde beveiligingsgegevens bevat.

      Deze gegevens worden gebruikt via AVE V11 API om autorisatiebevestiging te verkrijgen van de Flash Runtime Player. Als de bytearray geen inhoud bevat, gebruikt u in plaats daarvan de procedure om te zoeken naar een token-bestand voor één domein.
   1. Gebruiken `AuthorizedFeatureHelper.loadFeatureFromData` om de vereiste gegevens op te halen uit de bytearray.
   1. Het gereedschap verwijderen [!DNL .swf] bestand.

   De volgende voorbeelden laten zien hoe u een meervoudig token kunt gebruiken [!DNL .swf] bestand.

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
