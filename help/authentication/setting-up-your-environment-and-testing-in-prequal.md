---
title: Uw omgeving instellen en testen in een proefversie
description: Uw omgeving instellen en testen in een proefversie
exl-id: f822c0a1-045a-401f-a44f-742ed25bfcdc
source-git-commit: bfc3ba55c99daba561255760baf273b6538a3c6e
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Uw omgeving instellen en testen in een proefversie{#setting-up-your-environment-and-testing-in-prequal}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

Het doel van deze technische notitie is onze partners te helpen hun omgeving op te zetten en te beginnen met het testen van een nieuwe build die is geïmplementeerd op de Adobe-voorkwalificatieomgeving.

Omdat er twee buildflessen zijn: ***productie*** en ***fasering*** In dit document zullen we ons richten op de productie-instelling, met de vermelding dat alle stappen hetzelfde zijn voor opvoeren. Alleen de URL&#39;s zijn verschillend.

Stap 1 en 2 zetten de testomgeving op een van de testmachines in, stap 3 is een verificatie van de basisstroom en stap 4 en 5 geven enkele testrichtsnoeren.

>[!IMPORTANT]
>
> Het is erg belangrijk om stap 1 en 2 uit te voeren telkens als u uw testomgeving wilt veranderen (van het opvoeren naar het productieprofiel of andersom)
 

## STAP 1. Het oplossen van het domein van de pas aan IP {#resolving-pass-domain-to-an-ip}

* Voer de volgende opdracht uit om een IP van het taakverdelingsmechanisme te zoeken die voor spoofing kan worden gebruikt:

* **Op Windows**

   ```cmd
   C:\>nslookup sp-prequal.auth.adobe.com
   ...
   Addresses:  52.13.71.11
               54.184.208.150
   ```

```Choose any IP from **addresses** section (e.g. `52.13.71.11)```

* **Op Linux/Mac**

```sh
    $ dig sp-prequal.auth.adobe.com
    
    ;; ANSWER SECTION:
    ...
    ............ 60 IN A      52.13.71.11
    ............ 60 IN A      54.184.208.150
```

```Choose any IP from **A records (**e.g `52.13.71.11)```

>[!NOTE]
>
>Domeinen die van het antwoord zijn uitgesloten omdat ze niet relevant zijn en van gebruiker tot gebruiker kunnen verschillen.

>[!IMPORTANT]
>
> Deze IP adressen kunnen in de toekomst veranderen en zij zouden niet het zelfde voor gebruikers in verschillende geografische gebieden kunnen zijn.


## STAP 2.  De prekwalificatie van de productieomgeving {#spoofing-the-prequalification-environment}

* Bewerk de *c:\\windows\\System32\\drivers\\etc\\hosts* bestand (in Windows) of */etc/hosts* bestand (op Macintosh/Linux/Android) en voeg het volgende toe:

* Profiel van steunkleuren
   * 52.13.71.11 http://entitlement.auth.adobe.com, http://sp.auth.adobe.com, http://api.auth.adobe.com

**Gesproken tekst op Android:** Als u wilt dat Android wordt gebruikt, moet u een Android-emulator gebruiken.

* Zodra spoofing op zijn plaats is, kunt u de regelmatige URLs voor de productie en het opvoeren profielen eenvoudig gebruiken: (d.w.z. `http://sp.auth-staging.adobe.com` en `http://entitlement.auth-staging.adobe.com` en je raakt de *voorkwalificatieomgeving/productie* van de* nieuwe build.


## STAP 3.  Controleren of u naar de juiste omgeving wijst {#Verify-you-are-pointing-to-the-right-environment}

**Dit is een eenvoudige stap:**

* load [voorkómen van rechten](https://entitlement-prequal.auth.adobe.com/environment.html) en [aanspraak](https://entitlement.auth.adobe.com/environment.html). Ze zouden dezelfde reactie moeten teruggeven.


## STAP 4.  Voer een eenvoudige authentificatie/vergunningsstroom uit gebruikend de website van de programmeur {#peform-a-simple-auth-flow}

* Deze stap vereist het de websiteadres van de programmeur en sommige geldige geloofsbrieven MVPD (een gebruiker dat het voor authentiek en geautoriseerd is).

## STAP 5.  Scènetests uitvoeren met de websites van de programmeur {#perform-scenario-testing-using-programmer-website}

* Na de voltooiing van de milieu opstelling en het verzekeren dat de basisauthentificatie-vergunning stroom werkt kunt u met het testen van complexere scenario&#39;s te werk gaan.


## STAP 6.  Testen met de API-testsite {#perform-testing-using-api-testing-site}

* Als u dieper wilt gaan in het testen van de authentificatie van Adobe Primetime, adviseren wij u gebruiken [API-testsite](http://entitlement-prequal.auth.adobe.com/apitest/api.html).

Meer informatie vindt u op de API-testsite op [Hoe te om de stromen van de Vergunning van de Authentificatie te testen gebruikend Adobe API testplaats](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).
