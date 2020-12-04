---
seo-title: Een gebruikersinterface voor verificatie maken
title: Een gebruikersinterface voor verificatie maken
uuid: 4744bac0-c36e-4b0a-b3fb-d81c7f2e7617
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Een gebruikersinterface voor verificatie maken {#create-an-authentication-ui}

1. Maak een gebruikersinterface om de verificatiereferenties van de gebruiker op te halen.

   Hieronder ziet u een Flex-voorbeeld van een eenvoudige gebruikersinterface voor het ophalen van gebruikersgegevens. Het bestaat uit een deelvensterobject met twee `TextInput`-objecten, één voor elke gebruikersnaam en wachtwoord. Het deelvenster bevat ook een knop waarmee de methode `credentials()` wordt gestart.

   ```xml
   <mx:Panel x="236.5"  
             y="113"  
             width="325"  
             height="204"  
             layout="absolute"  
             title="Login">  
       <mx:TextInput x="110"  
                     y="46"  
                     id="uName"/>  
       <mx:TextInput x="110"  
                     y="76"  
                     id="pWord"  
                     displayAsPassword="true"/>  
       <mx:Text x="35"  
                y="48"  
                text="Username:"/>  
       <mx:Text x="35"  
                y="78"  
                text="Password:"/>  
       <mx:Button x="120"  
                  y="115"  
                  label="Login"  
                  click="credentials()"/>  
   </mx:Panel>  
   ```

1. Schrijf de methode `credentials()` om de door de gebruiker opgegeven verificatiewaarden te verwerken.

   De methode `credentials()` is een door de gebruiker gedefinieerde methode die de waarden voor gebruikersnaam en wachtwoord doorgeeft aan de methode `setDRMAuthenticationCredentials()`. Nadat de waarden zijn doorgegeven, herstelt de methode `credentials()` de waarden van de objecten `TextInput`.

   ```
   <mx:Script> 
       <![CDATA[ 
         public function credentials():void { 
             videoStream.setDRMAuthenticationCredentials(uName, pWord, "drm"); 
             uName.text = ""; 
             pWord.text = ""; 
   } ]]> 
   </mx:Script> 
   ```

   U kunt dit type eenvoudige interface implementeren door het deelvenster als onderdeel van een nieuwe status op te nemen. De nieuwe status komt voort uit de basisstatus wanneer het object `DRMAuthenticateEvent` wordt gegenereerd. Het volgende voorbeeld bevat een `VideoDisplay`-object met een bronkenmerk dat naar een beveiligd videobestand wijst. In dit geval wordt de methode `credentials()` gewijzigd zodat de toepassing ook naar de basisstatus wordt geretourneerd. Deze methode doet dit nadat de gebruikersgegevens zijn doorgegeven en de waarden van het TextInput-object opnieuw zijn ingesteld.

   ```xml
   <?xml version="1.0" encoding="utf-8"?> 
   <mx:WindowedApplication xmlns:mx="https://www.adobe.com/2006/mxml" 
       layout="absolute" 
       width="800" 
       height="500" 
       title="DRM FLV Player" 
       creationComplete="initApp()" > 
       <mx:states> 
           <mx:State name="LOGIN"> 
               <mx:AddChild position="lastChild"> 
                       <mx:Panel x="236.5"  
                                 y="113"  
                                 width="325"  
                                 height="204"  
                                 layout="absolute"  
                                 title="Login"> 
                       <mx:TextInput x="110"  
                                     y="46"  
                                     id="uName"/> 
                       <mx:TextInput x="110"  
                                     y="76"  
                                     id="pWord"  
                                     displayAsPassword="true"/> 
                       <mx:Text x="35"  
                                y="48"  
                                text="Username:"/> 
                       <mx:Text x="35"  
                                y="78"  
                                text="Password:"/> 
                       <mx:Button x="120"  
                                  y="115"  
                                  label="Login"  
                                  click="credentials()"/> 
                       <mx:Button x="193"  
                                  y="115"  
                                  label="Reset"  
                                  click="uName.text=''; 
               </mx:Panel> 
           </mx:AddChild> 
       </mx:State> 
   </mx:states> 
   pWord.text='';"/> 
   
   <mx:Script> 
       <![CDATA[ 
           import flash.events.DRMAuthenticateEvent; 
           private function initApp():void { 
               videoStream.addEventListener(DRMAuthenticateEvent.DRM_AUTHENTICATE, 
                                            drmAuthenticateEventHandler); 
           } 
           public function credentials():void { 
               videoStream.setDRMAuthenticationCredentials(uName, pWord, "drm"); 
               uName.text = ""; 
               pWord.text = ""; 
               currentState=''; 
           } 
           private function drmAuthenticateEventHandler(event:DRMAuthenticateEvent):void { 
               currentState='LOGIN'; 
           } 
       ]]> 
   </mx:Script> 
   <mx:VideoDisplay id="video"  
                    x="50"  
                    y="25"  
                    width="700"  
                    height="350" 
                    autoPlay="true" 
                    bufferTime="10.0" 
                    source="https://www.example.com/flv/Video.flv" /> 
   </mx:WindowedApplication> 
   ```

