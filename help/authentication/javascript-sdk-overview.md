---
title: JavaScript SDK - Overzicht
description: JavaScript SDK - Overzicht
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# JavaScript SDK - Overzicht {#javascript-sdk-overview}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Inleiding

De Adobe adviseert hoogst dat u aan recentste JS v4.x van de bibliotheek AccessEnabler migreert.

De Adobe Primetime-verificatie-JavaScript-integratie biedt programmeurs een oplossing op tv-elke locatie in de vertrouwde ontwikkelomgeving van JS-webtoepassingen. De belangrijkste componenten van de integratie zijn uw &quot;high-level&quot;toepassing (gebruikersinteractie, videopresentatie), en de Adobe-geleverde &quot;laag-niveau&quot;bibliotheek AccessEnabler die uw ingang aan de machtigingsstromen verstrekt, en communicatie met de authentificatieservers van Adobe Primetime behandelt.

De algemene Adobe Primetime-verificatierechten worden behandeld in [Machtigingsstroom voor programmeur](/help/authentication/entitlement-flow.md)en de JavaScript Integration Cookbook doorloopt de implementatie. De volgende secties verstrekken beschrijvingen en steekproeven specifiek voor de integratie JavaScript AccessEnabler.

>[!IMPORTANT]
>
>In dit document wordt de implementatie voor een desktopweboplossing beschreven. De JavaScript-bibliotheek wordt niet ondersteund op mobiele platforms (bijvoorbeeld Safari op iOS, Chrome op Android). Gebruik onze native SDK&#39;s als u een mobiel platform (iOS, Android, Windows) als doel wilt instellen.

## Het dialoogvenster MVPD-selectie maken {#creating-the-mvpd-selection-dialog}

Om een gebruiker aan login aan hun MVPD en voor authentiek verklaard te worden, moet uw pagina of speler een manier voor de gebruiker verstrekken om hun MVPD te identificeren. Een standaardversie van een MVPD selectiedialoog wordt verstrekt voor ontwikkeling. Voor productiegebruik, moet u uw eigen selecteur uitvoeren MVPD.

Als u al weet wie de leverancier van de klant is, kunt u [plaats programmatically MVPD](/help/authentication/home.md), zonder gebruikersinteractie. De techniek is het zelfde, maar negeert de stap om het de dialoogvakje van de Selecteur van de Leverancier aan te halen en de klant te vragen om hun MVPD te selecteren.

## De serviceprovider weergeven {#displaying-the-service-provider}

Het volgende codevoorbeeld toont aan hoe te om de dienstverlener voor de huidige klant te ontdekken en te tonen:

**HTML** - Deze pagina voegt een sectie aan de pagina toe die de gekozen leverancier van de klant toont, als zij reeds het programma worden geopend:

```HTML
    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
            "http://www.w3.org/TR/html4/loose.dtd"> 
    <html>
    <head>
        <title>Get the distributor that is used for the authentication</title>
        <script type="text/javascript" src="libs/jquery-1.4.4.min.js"></script>
        <script type="text/javascript" src="libs/swfobject.js"></script>
        <script type="text/javascript" src="scripts/sample6.js"></script>
    </head>
    <body>
        <div id="alternative">
        <a href="http://www.adobe.com/go/getflashplayer"> 
            <img src="http://www.adobe.com/images/shared/download_buttons/get_flash_player.gif" 
                 alt="Get Adobe Flash player"/> </a>
        </div> 
        <div id="user_authenticated">Please wait while we verify your authentication status</div> 
        <div id="control">
        <button id="sign_in" style="display:none;">Sign in</button>
        <button id="sign_out" style="display:none;">Sign out</button>
        </div> 
        <div id="distributor"></div> 
        <div id="provider_selector" style="display:none;">
        <select id="provider_list"></select>
        <button id="login">Login</button>
        <button id="cancel">Cancel</button>
        </div> 
        <div id="video_player">This is a video player showing an image as a preview.  You are not yet authorized to see this content.  Make sure that you first sign in.
        </div> 
        <div id="get_authorization">
        <button id="request_access" style="display:none;">Request access</button>
        </div> 
    </body>
    </html>
```


**JavaScript** Dit JavaScript-bestand vraagt de Access Enabler naar de huidige provider als de gebruiker al is aangemeld en geeft het resultaat weer in de paginasectie die voor deze provider is gereserveerd. Het voert ook een MVPD selecteerdialoog uit:

```JS
    $(function() {
        embedAE();
    }); 
    function embedAE() {
        var flashvars = {};
        var params = {
            bgcolor: "#869ca7",
            quality: "high",
            allowscriptaccess: "always"
        };
        var attributes = {
            id: "ae_swf",
            align: "middle",
            name: "ae_swf"
        };
        swfobject.embedSWF(
                "https://entitlement.auth-staging.adobe.com/entitlement/AccessEnabler.swf",      
                "alternative", "1", "1", "10.1.53", "", flashvars, params, attributes);
    } 
    function getAE() {
        return document.getElementById("ae_swf");
    } 
    function swfLoaded() {
        var swf = getAE();
        initBindings();
        // don't load the default provider-selection dialog 
        swf.setProviderDialogURL("none");
        // identify yourself 
        swf.setRequestor("sample_requestor_Id");
        swf.checkAuthentication();
    } 
    // Define the button actions for the provider dialog
    function initBindings() {
        var provider_selector = $('#provider_selector');
        var sign_in = $('#sign_in');
        var sign_out = $('#sign_out');
        var login = $('#login');
        var cancel = $('#cancel');
        var request_access = $('#request_access'); 
        sign_out.click(function() {
            getAE().logout();
        });
        sign_in.click(function() {
            getAE().getAuthentication();
        }); 
        login.click(function() {
            var selected_mvpd_id = $("#provider_list option:selected").val();
            getAE().setSelectedProvider(selected_mvpd_id);
        }); 
        cancel.click(function() {
            getAE().setSelectedProvider(null);
            provider_selector.hide();
        }); 
        request_access.click(function(){
            getAE().getAuthorization("sample_requestor_Id");
        });
    }
    // Called if user is already authenticated; queries AE to find the current user's MVPD, 
    // Adds the result to the UI 
    function setDistributor() {
        var distributor = $("#distributor");
        var selectedProvider = getAE().getSelectedProvider();
        distributor.replaceWith('<div id="distributor">' +
                                'Courtesy of ' +
                                selectedProvider.MVPD +
                                '</div>');
    } 
    // Adjust the contents of the provider dialog, based on authentication status 
    // Adds the call to check and display the current distributor, if the user is already
    // logged in. 
    function setAuthenticationStatus(isAuthenticated, errorCode) {
        var user_authenticated = $("#user_authenticated");
        var video_player = $("#video_player");
        var sign_in = $('#sign_in');
        var sign_out = $('#sign_out');
        var request_access = $('#request_access'); 
        if (isAuthenticated == 1) {
            setDistributor();
            user_authenticated.replaceWith('<div id="user_authenticated">
                                           You are authenticated - if you wish you can sign out
                                           </div>');
            sign_out.show();
            sign_in.hide();
            video_player.replaceWith('<div id="video_player">Now you can ask for access.</div>');
            request_access.show();
        } else {
            user_authenticated.replaceWith('<div id="user_authenticated">
                                           You are not authenticated please sign in
                                           </div>');
            sign_in.show();
            sign_out.hide();
        }
    } 
    // Allow user to choose a provider 
    function displayProviderDialog(providers) {
        var provider_list = $("#provider_list");
        var options = provider_list.attr('options');
        for (var index in providers) {
            options[index] = new Option(providers[index].displayName,
                                        providers[index].ID);
        }
        //select the first one by default 
        if (!$("#provider_list option:selected").length)
            $("#provider_list option[0]").attr('selected', 'selected'); 
        $('#provider_selector').show();
    } 
    // Handle the authorization response by sending token to video player 
    function setToken(requested_resource_id, token) {
        var video_player = $("#video_player");
        var request_access = $("#request_access");
        video_player.replaceWith('<div id="video_player">Now you are authorized to ' +
                                 requested_resource_id +
                                 ' content with ' + token + ' . </div>');
    }
```

## Afmelden {#logout}

Bellen `logout()` om het logout-proces te starten. Deze methode gebruikt geen argumenten. Het logout de huidige gebruiker, die alle authentificatie en vergunningsinformatie voor die gebruiker ontruimt en alle tokens AuthN en AuthZ van het lokale systeem schrapt.

In sommige gevallen is de speler niet verantwoordelijk voor het afhandelen van gebruikersaanmeldingen:



- **Wanneer de logout van een plaats in werking wordt gesteld die niet met de authentificatie van Adobe Primetime wordt geïntegreerd.** In dit geval kan de MVPD de Adobe Primetime-verificatie Single Logout-service aanroepen via een omleiding van de browser. (Het aanroepen van SLO via een backchannel-aanroep wordt momenteel niet ondersteund.)

>[!NOTE]
>
>Als de gebruiker de computer lang genoeg inactief laat om de tokens te laten verlopen, kan hij of zij nog steeds terugkeren naar zijn of haar sessie en met succes het afmelden starten. De authentificatie van Adobe Primetime zorgt ervoor dat alle tokens worden geschrapt en MVPD meedeelt om hun zitting te schrappen, eveneens.

De volgende JavaScript-code demonstreert het afmelden (verifiëren) van een momenteel geverifieerde gebruiker:

```JS
    [...]
    /*
     * @param isAuthenticated authentication status: 1 - Authenticated, 0 - not authenticated 
     * @param errorCode Any error that occurred when determining the authentication status.
     * An empty string if no error occurred.
     */
    function setAuthenticationStatus(isAuthenticated, errorCode) {
        if (isAuthenticated == 1 ) {
            /* User is authenticated – we can logout / deauthenticate */
            accessEnablerObject.logout();
            /* Logs out the current user, clearing all authentication
             * and authorization information for that user. Deletes
             * all authN and authZ tokens from the user's system.
             */
        } else {
            /*
             * User is NOT authenticated – we do not need to logout;
             * Show the log-in image/button/message
             */
        }
    }
```

<!--
**Related Information**

- [JavaScript SDK Cookbook](/help/authentication/javascript-sdk-cookbook.md)
- [JavaScript SDK API Reference](/help/authentication/javascript-sdk-api-reference.md)
- [JavaScript Code Samples](#javascript-code-samples)
- [Understanding Tokens](#understanding_tokens)
-->
