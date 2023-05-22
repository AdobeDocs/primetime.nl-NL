---
title: Hoe te om de MVPD Login Pagina van iFrame aan Popup te migreren
description: Hoe te om de MVPD Login Pagina van iFrame aan Popup te migreren
exl-id: 389ea0ea-4e18-4c2e-a527-c84bffd808b4
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---

# Hoe te om de MVPD login pagina van iFrame aan Popup te migreren {#migr-mvpd-login-iframe-popup}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Pop-up en iFrame {#popup-vs-iframe}

Sommige gebruikers hebben cookie-problemen van derden aangetroffen bij de iFrame-implementatie van een MVPD-aanmeldingspagina.
<!--These issues are described in the tech notes linked below:

* [Adobe Primetime authentication and Safari login issues](https://tve.helpdocsonline.com/adobe-pass)
* [MVPD iFrame login and 3rd party cookies](https://tve.helpdocsonline.com/mvpd)-->

Het Adobe Primetime-verificatieteam **raadt u aan de aanmeldingspagina voor pop-up / nieuw venster te implementeren** in plaats van de iFrame-versie op Firefox en Safari.  Als u echter een aanmeldingspagina voor Internet Explorer implementeert, kunnen er problemen optreden met de popup-implementatie. De IE kwesties worden veroorzaakt door het feit dat, nadat de gebruiker met hun MVPD in popup venster voor authentiek verklaart, de authentificatie van Adobe Primetime een ouderpagina redirect dwingt, die als popup blokker door Internet Explorer wordt gezien. Het Adobe Primetime-verificatieteam **raadt u aan de iFrame-aanmelding voor Internet Explorer te implementeren**.

De voorbeeldcode in deze technische notitie maakt gebruik van een hybride implementatie van zowel iFrame als popup: een iFrame openen in Internet Explorer en een pop-up openen in de andere browsers.

Aangezien er al een iFrame-implementatie bestaat, bevat het eerste deel van de technische notitie de code voor de iFrame-implementatie en het tweede deel de wijzigingen die nodig zijn om de popup-implementatie als standaard aan te passen.


## MVPD-kiezer met aanmeldingspagina in iFrame {#mvpd-pickr-iframe}

De vorige codevoorbeelden toonden een pagina van de HTML die bevat &lt;div> -tag waar het iFrame samen met de knop Close iFrame wordt gemaakt:

```HTML
<body> 
    <div id="mvpddiv">
        <div style="background: red">
            <input type="button" id="btnCloseIframe" value="X" onclick="closeIframeAction();">
        </div>
        <br/>
        <!-- We use the "about:blank" value so that when the iFrame loads
             we do not see the the parent page. -->
        <iframe id="mvpdframe" name="mvpdframe" src="about:blank"></iframe>
    </div> 
</body>
```

Hier is het bijbehorende **JavaScript** code:

```JavaScript
/*
 * Callback indicating that the AccessEnabler swf has initialized
 */
function swfLoaded() {
    // AccessEnabler is loaded so we can use the API function it provides
    accessEnablerObject.setRequestor(requestorID); 
    accessEnablerObject.checkAuthentication();
} 
/*
* The code the correctly closes the opened IFrame and does not leave the
* AccessEnabler in an undefined state.
*/
function closeIframeAction () {
    accessEnablerObject.setSelectedProvider(null);
    /* We use the "about:blank" value so that when the iFrame loads
     * we do not see the the previous MVPD.
     */
    document.getElementById('mvpdframe').src="about:blank";
    document.getElementById('mvpddiv').style.visibility="hidden";
    document.getElementById('mvpddiv').style.display="none";
}
/*
* Some of the supported MVPDs require their login pages to be displayed within an iFrame.
* In your HTML page, you must include the following <div> tag: "<div id="mvpddiv"></div>".
* Called when the selected MVPD requires an iFrame in which to display its authentication UI.
*/
function createIFrame(inWidth, inHeight) {
     // Create the iFrame to the specified width and height for the auth page
    ifrm = document.createElement("IFRAME");
    ifrm.name = "mvpdframe";
    ...
    document.getElementById('mvpddiv').appendChild(ifrm);
    ...
    // Force the name into the DOM since it is still not refreshed, for IE
    window.frames["mvpdframe"].name = "mvpdframe";
}
/*
 * The custom non-Flash MVPD selector dialog will be implemented in this function.
 */
function displayProviderDialog(providers) {
    /* This is an example how previously the MVPD picker was build and will be replaced. */
}
/* 
* Sending the user selected MVPD of the custom dialog is achieved
* by calling the API function setSelectedProvider(providerID:String).
*/
function setSelectedProvider(providerID) {
    accessEnablerObject.setSelectedProvider(providerID);
}
```


## MVPD-kiezer met aanmeldingspagina in pop-upvenster {#mvpd-pickr-popup}

Omdat we geen **iFrame** nu bevat de HTML-code niet de iFrame of de knop om het iFrame te sluiten. De div die voorheen de iFrame bevatte - **mvpddiv** - wordt bewaard en gebruikt voor:

* om de gebruiker te laten weten dat de MVPD-aanmeldingspagina al is geopend als de popup-focus niet meer aanwezig is
* om een koppeling te maken om de focus op de popup te herstellen

```HTML
<body onload="javascript:loadAccessEnabler();"> 
   <div id="aeHolder">
       <div name="contentAccessEnabler" id="contentAccessEnabler"></div>
   </div>
   <div id="mvpddiv">
      <p>
      <strong>No login window?</strong>
      <br/>
      <a href="javascript:mvpdWindow.focus();">Click here to open it.</a>
      <br/>
      Still not working? Check popup blockers!
      </p>
   </div> 
 
   <div id="picker" style="display:none">
      Choose MVPD: <br/>
      <select id="mvpdList" multiple></select>
      <br/>
         <a id="authenticateButton" onclick="javascript:authenticate();">Authenticate</a>
   </div>
</body>
```

De lijst van MVPDs zal in geroepen div worden getoond **kiezer** als een selectie **-mvpdList**.

Een nieuwe API callback zal worden gebruikt - **setConfig(configXML)**. De callback wordt geactiveerd na het aanroepen van de functie setRequestor(requestID). Deze callback keert de lijst van MVPDs terug die met aanvragerID eerder wordt geïntegreerd. In de callback methode, zal inkomende XML worden ontleed, en de lijst van MVPDs caching. De plukker MVPD wordt ook gecreeerd maar niet getoond.

```JavaScript
var mvpdList;  // The list of cached MVPDs
var mvpdWindow;  // The reference to the popup with the MVPD login page
var cancelTimer = 0;
/* Callback indicating that the AccessEnabler swf has initialized */
function swfLoaded() {
   accessEnablerObject = $('#AccessEnabler').get(0);
   // Using a custom implementation of the MVPD picker
   accessEnablerObject.setProviderDialogURL('none');
   accessEnablerObject.setRequestor(requestorID); 
}

function setConfig(configXML) {
   mvpdList = [];
   $.each($($.parseXML(configXML)).find('mvpd'), function (idx, item) {
      var mvpdId = $(item).find('id').text();
      mvpdList[mvpdId] = {
         displayName: $(item).find('displayName').text(),
         logo: $(item).find('logoUrl').text(),
         popup: $(item).find('iFrameRequired').text() == "true",
         width: $(item).find('iFrameWidth').text(),
         height: $(item).find('iFrameHeight').text()
      };

      $('#mvpdList').append($('<option value="' + mvpdId + '" title="' + mvpdId + '">' + mvpdList[mvpdId].displayName + '</option>'));
   });
   accessEnablerObject.getAuthentication();
}
```

Nadat de functie getAuthentication() of getAuthorization() is aangeroepen, wordt de callback displayProviderDialog() geactiveerd. Normaal, binnen deze callback, zou de lijst MVPD gebouwd en getoond zijn geweest. Aangezien de plukker MVPD reeds wordt gebouwd, is het enige resterende ding om het aan de gebruiker te tonen.

```JavaScript
/*
 * The custom non-Flash MVPD selector dialog will be implemented in this function.
 */
function displayProviderDialog(providers) {
   $('#picker').show();
}
```

Nadat de gebruiker een MVPD van de plukker heeft geselecteerd, moet popup worden gecreeerd. Sommige browsers kunnen popup blokkeren als het met ongeveer:blank of met een pagina wordt gecreeerd die op een ander domein is - daarom wordt het geadviseerd om het met hostname van te openen waar AccessEnabler wordt geladen.

In de iFrame-implementatie werd het opnieuw instellen van de verificatiestroom uitgevoerd door de knop btnCloseIframe en de JavaScript-functie closeIframeAction(), maar nu is het niet meer mogelijk het iFrame te versieren. Zo, wordt het zelfde gedrag bereikt door te letten op wanneer popup (of door de gebruiker of door de authentificatiestroom te voltooien) wordt gesloten. Er is een codefragment toegevoegd dat ook helpt als de gebruiker de focus van de pop-up verliest:

```HTML
"<a href="javascript:mvpdWindow.focus();">Click here to open it.</a>".
```

Bij de createIFrame()-callback wordt de **mvpddiv** div wordt weergegeven.

```JavaScript
function createIFrame(width, height) {
   $('#mvpddiv').show();
   if (useIframeLoginStyle) {
      ...
   }
}

/* Function called when user has selected the MVPD from the picker */
function authenticate() {
   var selectedMvpd = $('#mvpdList').val()[0];
   if (mvpdList[selectedMvpd].popup) {
      mvpdWindow = window.open("http://entitlement.auth-staging.adobe.com", "mvpdframe", "width=" + mvpdList[selectedMvpd].width + ",height=" + mvpdList[selectedMvpd].height, true);
      if (!mvpdWindow) {
         // Message to user that popup blocker is not allowing the authentication process to start
      }
      //watch the mvpd popup for close
      clearInterval(cancelTimer);
      cancelTimer = setInterval(checkClosed, 200);
   }
   accessEnablerObject.setSelectedProvider(selectedMvpd);
}

function checkClosed() {
   try {
      if (mvpdWindow && mvpdWindow["closed"]) {
         clearInterval(cancelTimer);
         accessEnablerObject.setSelectedProvider(null);
         accessEnablerObject.getAuthentication();
         $('#mvpddiv').hide();
      }
   } catch (error) {
      console.log(error);
   }
}
```

>[!IMPORTANT]
>
>* De voorbeeldcode bevat een hardcoded variabele voor de gebruikte requestID - &#39;REF&#39;, die moet worden vervangen door een echte id van de programmeur.
>* De voorbeeldcode wordt alleen correct uitgevoerd vanuit een zwevend domein dat is gekoppeld aan de gebruikte aanvrager-id.
>* Aangezien de gehele code kan worden gedownload, is de code in deze technische notitie afgebroken. Voor een volledig monster raadpleegt u **JS iFrame versus pop-upvoorbeeld**.
>* De externe JavaScript-bibliotheken zijn gekoppeld vanuit [Google Hosted Services](https://developers.google.com/speed/libraries/).

