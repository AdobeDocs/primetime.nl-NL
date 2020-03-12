---
description: Pas uw referentie-implementatie aan om Adobe Primetime-verificatie te integreren voor uw productieomgeving.
seo-description: Pas uw referentie-implementatie aan om Adobe Primetime-verificatie te integreren voor uw productieomgeving.
seo-title: Primetime-verificatie integreren
title: Primetime-verificatie integreren
uuid: 34cdf1da-261e-462c-a194-4fcb439e5dfb
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Primetime-verificatie integreren {#integrate-primetime-authentication}

Pas uw referentie-implementatie aan om Adobe Primetime-verificatie te integreren voor uw productieomgeving.

De integratie van de Dienst van de Uitvoering van de Verwijzing van de Echtheid Primetime werkt uit-van-de-doos als demonstratie. Nochtans, om de integratie in een productie-klaar speler te gebruiken, moet u de volgende aanpassingen uitvoeren:

1. Machtigingsstromen in- of uitschakelen.

   De `EntitlementManager` moet eerst een geval van de authentificatieSDK initialiseren en verkrijgen Primetime om worden toegelaten. Als de gebruiker deze bibliotheek `EntitlementManager` niet initialiseert, wordt de manager uitgeschakeld.
1. De toepassing inschakelen `EntitlementManger`, vanuit de hoofdtoepassingsklasse:

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. Gebruik de `ManagerFactory` klasse om een instantie van de `EntitlementManager`klasse te verkrijgen.

   U moet het altijd gebruiken `ManagerFactory` om een instantie van de toepassing te krijgen, `EntitlementManager`aangezien `ManagerFactory` handhaaft één enkel geval van EntitlementManager voor uw toepassing. Instantieer nooit de `EntitlementManager` of de `EntitlementManagerOn` klassen door hun aannemers te gebruiken.

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   De `ManagerFactory` functie retourneert een instantie van `EntitlementManagerOn`, met de machtigingsstromen ingeschakeld, als u eerder hebt aangeroepen `EntitlementManager.initializeAccessEnabler`. Als u niet eerst roept `EntitlementManager.initializeAccessEnabler`, dan `ManagerFactory` zal een geval van terugkeren `EntitlementManager`, met de machtigingsstromen gehandicapt. 1. Configureer de aanvrager-id.

   De implementatie van de Verwijzing wordt vooraf geconfigureerd met de id van de testaanvrager ingesteld op: &quot;REF&quot;. U kunt deze aanvrager-id gebruiken om uw toepassing te testen. Wanneer u klaar bent om de ID van de Aanvrager te gebruiken die door uw vertegenwoordiger van de Authentificatie wordt verstrekt Primetime, werk het [!DNL res/values/strings.xml] dossier van de toepassing met uw identiteitskaart van de Aanvrager bij.

   ```xml
   <!-- Programmer Requestor ID, change to ID provided by your Adobe  
        Primetime pay-TV pass representative --> 
   <string name="adobepass_requestor_id">REF</string> 
   
   <!-- Adobe Primetime pay-TV pass service provider endpoint for production 
        environment --> 
   <string name="adobepass_sp_url_production">sp.auth.adobe.com</string> 
   
   <!-- Adobe Primetime pay-TV pass service provider endpoint for staging  
        environment --> 
   <string name="adobepass_sp_url_staging">sp.auth-staging.adobe.com</string>
   ```

   Bovendien moet u mogelijk de URL&#39;s wijzigen die uw toepassing gebruikt om verbinding te maken met de Primetime-verificatieservices. Dit zijn onder andere de URL&#39;s van de Primetime-verificatieserver en productieserver, en een URL naar een token-verificatieservice. Raadpleeg uw Adobe Primetime-vertegenwoordiger voor meer informatie. 1. Onderteken de aanvrager-id.

   Om de identiteit van de programmeur binnen het authentificatiesysteem te vestigen Primetime, wordt de identiteitskaart van de Aanvrager van de Programma verzonden naar het authentificatiesysteem Primetime. Als extra beveiligingslaag moet de aanvrager-id door de programmeur worden ondertekend voordat u deze naar Adobe kunt verzenden. Adobe raadt de programmeur aan een service in te stellen om de aanvrager-id op een vertrouwd netwerk te ondertekenen.

   In de Primetime-referentieimplementatie wordt getoond hoe u de id van de aanvrager ondertekent. Dit is echter alleen voor demonstratiedoeleinden. Adobe raadt u ten zeerste aan het handtekeningcertificaat en de code van de handtekeninggenerator, onder `com.adobe.primetime.reference.crypto`, niet in een productietoepassing op te nemen. In plaats daarvan moet u de toepassing verplaatsen naar een vertrouwde netwerkservice.

1. Configureer de serveromgeving.

   De Primetime authentificatieservice kan in twee afzonderlijke milieu&#39;s lopen:

   * Staging - De testomgeving wordt gebruikt voor het testen van uw toepassing.
   * Productie - De productieomgeving wordt gebruikt voor live implementaties van uw toepassing.
   U stelt de URI&#39;s voor zowel de testomgeving als de productieomgeving in met de toepassing. U moet echter instellen welke van deze URI&#39;s door de toepassing in de code wordt gebruikt. In de `com.adobe.primetime.reference.manager.EntitlementManger` klasse, plaats de `environmentUri` variabele aan of `STAGING_URI` of `PRODUCTION_URI` afhankelijk van welke milieu van de authentificatiedienst Primetime u gebruikt.

   >[!NOTE]
   >
   >De opgegeven aanvrager-id (&quot;REF&quot;) mag alleen worden gebruikt in de testomgeving.

   `com.adobe.primetime.reference.manager.EntitlementManager`:

   ```java
     // Adobe Primetime authentication service provider endpoint for production environment 
     PRODUCTION_URI = 
         application.getResources().getString(R.string.adobepass_sp_url_production); 
   
     // Adobe Primetime authentication service provider endpoint for staging environment 
     STAGING_URI = 
       application.getResources().getString(R.string.adobepass_sp_url_staging); 
   
     // Set to STAGING_URI when testing against the staging/test environment 
     // Set to PRODUCTION_URI when deploying the application for production use 
     String environmentUri = STAGING_URI; 
   
     // Adobe Primetime authentication service URI used by this application 
     PAYTV_PASS_URI = environmentUri + "/adobe-services"; 
   
     // Token Verification Service URL 
     TVS_URL = "https://" + environmentUri + "/tvs/v1/validate";
   ```

1. Pas het raster voor MVPD-selectie aan.

   Op de selectiepagina van de inhoudprovider wordt een tabel weergegeven met de bovenste negen MVPD&#39;s die de gebruiker kan selecteren. De toepassing trekt top negen MVPDs van een bevolen lijst binnen de toepassing die beschikbare MVPDs aanpassen die met Programmer in het authentificatiesysteem Primetime wordt geïntegreerd. De geordende lijst van primaire MVPDs wordt gehouden op MVPD identiteitskaart binnen het authentificatiesysteem Primetime, niet de MVPD vertoningsnaam. Het is belangrijk om te verifiëren dat MVPD IDs in de primaire lijst MVPDs MVPD IDs met de rekening van de programmeur wordt geïntegreerd, aangezien in sommige gevallen IDs over integraties verschillend kan zijn. Hieronder ziet u de geordende lijst met primaire MVPD&#39;s in de klasse `com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment`.

   ```java
   /* Array of MVPDs to display in a Grid of icons 
   When displaying a grid, only the MVPDs which intersect this array and the 
   ArrayList of all MVPDs are displayed. 
   The array contents are ordered by display preference as only a maximum of 
   MAX_DISPLAY_ICONS are displayed. 
   */ 
   private static final String[] PRIMARY_MVPDS = { 
   "Comcast_SSO",                         // Comcast XFINITY 
   "DTV",                                 // DirectTV 
   "Dish",                                // Dish 
   "TWC",                                 // Time Warner Cable 
   "Cox",                                 // Cox 
   "Charter_Direct",                      // Charter 
   "Verizon",                             // Verizon FiOS 
   "Cablevision",                         // Cablevision Optimum 
   "ATT",                                 // AT&T U-verse 
   "Brighthouse",                         // Brighthouse 
   "Suddenlink",                          // Suddenlink 
   "Mediacom",                            // Mediacom 
   "CableOne",                            // CableOne 
   "WOW",                                 // WOW! 
   "RCN",                                 // RCN 
   "auth_atlanticbb_net",                 // Atlantic Broadband 
   "auth_armstrongmywire_com",            // Armstrong 
   "knology_auth-gateway_net",            // KNOLOGY 
   "serviceelectric_auth-gateway_net",    // Service Electric Cablevision 
   "msauth_midco_net",                    // Midcontinent Communications 
   "auth_metrocast_net",                  // MetroCast 
   "www_websso_mybrctv_com",              // Blue Ridge Communications 
   };
   ```

   De volgende lijst verstrekt een voorbeeld van hoe de geordende lijst van primaire MVPDs wordt gebruikt. De eerste kolom maakt een lijst van MVPDs die met Programmer wordt geïntegreerd. De tweede kolom is de (verkorte) geordende lijst van MVPDs. De derde kolom is de resultaatlijst die wordt gebruikt om de hoogste zes MVPDs aan de gebruiker te tonen.

   In dit voorbeeld worden de top zes MVPD&#39;s gebruikt in plaats van de daadwerkelijke negen, alleen om het voorbeeld eenvoudig te houden. U ziet hoe de resultatenlijst het snijpunt van de eerste twee lijsten bevat en dezelfde volgorde heeft als de tweede lijst. Ook, merk op dat AT&amp;T U-vers niet in de definitieve lijst is, aangezien slechts de eerste passende zes MVPDs worden genomen.

| Beschikbare MVPD&#39;s | Primaire MVPD&#39;s | Weergegeven 6 MVPD&#39;s |
|--- |--- |--- |
| <ol><li>XFINITEIT comprimeren</li><li>TWC</li><li>Mediacom</li><li>RCN</li><li>Dish</li><li>&amp;Omgekeerd</li><li>CableOne</li><li>Brighthouse</li><li>Atlantic Broadband</li><li>WOW!</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>Cablevision Optimum</li></ol> | <ol><li>XFINITEIT comprimeren</li><li>DirectTV</li><li>Dish</li><li> TWC</li><li>Cox</li><li>Handvest</li><li>Verizon FiOS</li><li>Cablevision Optimum</li><li>&amp;Omgekeerd</li></ol> | <ol><li>XFINITEIT comprimeren</li><li>DirectTV</li><li>Dish</li><li>TWC</li><li>Cox</li><li>Cablevision Optimum</li></ol> |
