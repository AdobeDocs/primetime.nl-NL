---
title: iOS/tvOS-toepassingsregistratie
description: iOS/tvOS-toepassingsregistratie
exl-id: 89ee6b5a-29fa-4396-bfc8-7651aa3d6826
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# iOS/tvOS-toepassingsregistratie {#iostvos-application-registration}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

## Inleiding {#Intro}

Vanaf versie 3.0 van de iOS/tvOS AccessEnabler SDK veranderen we het verificatiemechanisme met de servers van de Adobe. In plaats van het gebruiken van een openbare sleutel en een geheim systeem om requestorID te ondertekenen, introduceren wij het concept een het verklaringskoord van de Software dat kan worden gebruikt om een toegangstoken te verkrijgen dat later voor alle vraag wordt gebruikt die SDK aan onze servers maakt. Naast een software-instructie hebt u ook een aangepast URL-schema voor uw toepassing nodig.

Zie voor meer informatie [Dynamische clientregistratie](/help/authentication/dynamic-client-registration.md)

## Wat is een Software Statement? {#Soft_state}

Een verklaring van de Software is een teken JWT dat informatie over uw toepassing bevat. Elke toepassing moet een unieke software-instructie hebben die door onze servers wordt gebruikt om de toepassing in het systeem van de Adobe te identificeren. De verklaring van de Software moet worden overgegaan wanneer u AccessEnabler SDK initialiseert en het zal worden gebruikt om de toepassing met Adobe te registreren. Na registratie ontvangt de SDK een client-id en een clientgeheim die worden gebruikt om een toegangstoken te verkrijgen. Om het even welke vraag die SDK aan onze servers maakt zal een geldig toegangstoken vereisen. De SDK is verantwoordelijk voor het registreren van de toepassing, het verkrijgen en vernieuwen van het toegangstoken.

**Opmerking:** Een Softwareinstructie is toepassingsspecifiek en dezelfde softwareinstructie kan niet worden gebruikt voor meerdere toepassingen. Software-instructies op programmeerniveau volgen hetzelfde, dat wil zeggen ze kunnen alleen worden gebruikt voor één toepassing, of het nu om één kanaal of meerdere kanalen gaat. Deze beperking geldt ook voor aangepaste schema&#39;s.

## Hoe te om een Verklaring van de Software te verkrijgen? {#obtain}

### Als u toegang hebt tot het TVE-dashboard van de Adobe:

- Uw browser openen en naar <https://console.auth.adobe.com>
- Navigeren naar `Channels` en selecteert u het kanaal.
- Navigeren naar `Registered Applications` Tab.
- Klikken op `Add new application`.
- Geef een naam en een versie op voor uw toepassing en selecteer de platforms waarop deze beschikbaar zal zijn. iOS/tvOS in ons geval.
- Duw uw veranderingen aan de server en navigeer dan terug naar het Geregistreerde lusje van Toepassingen van het Kanaal.
- Er moet een lijst met alle geregistreerde toepassingen worden weergegeven. Klik op de knop   `Download` op de toepassing die u net hebt gemaakt. Mogelijk moet u een paar minuten wachten voordat de Software Statement wordt weergegeven. U kunt deze instructie dan downloaden.
- Er wordt een tekstbestand gedownload. Gebruik de inhoud ervan als de Software Statement.

Zie voor meer informatie [Dynamisch clientregistratiebeheer](/help/authentication/dynamic-client-registration-management.md).

### Als u geen toegang hebt tot het TVE-dashboard van de Adobe:

Een ticket verzenden naar <tve-support@adobe.com>. Neem alle benodigde informatie op, zoals kanaal, toepassingsnaam, versie en platforms. Iemand van ons ondersteuningsteam zal een softwareinstructie voor u maken.

## Hoe de Software Statement te gebruiken? {#use}

Nadat u uw Verklaring van de Software krijgt moet u het als parameter in de aannemer van Enabler van de Toegang overgaan. Wij adviseren het ontvangen van de Verklaring van de Software op een verre plaats. Op deze manier kunt u de Software Statement eenvoudig intrekken en wijzigen zonder een nieuwe versie van uw toepassing vrij te geven.

## Een aangepast URL-schema voor uw toepassing genereren {#generating}

### Als u toegang hebt tot het TVE-dashboard van de Adobe:

- Uw browser openen en naar <https://console.auth.adobe.com>
- Navigeren naar `Channels` en selecteert u het kanaal.
- Navigeren naar `Custom Schemes` Tab.
- Klikken op `Generate a new custom scheme`.
- Er wordt een nieuw aangepast schema voor uw toepassing gegenereerd. Voorbeeld: `adbe.1JqxQsYhQOCIrwPjaooY8w://`
- Breng de wijzigingen aan op de server.

### Als u geen toegang hebt tot het TVE-dashboard van de Adobe:

Een ticket verzenden naar <tve-support@adobe.com>. Neem kanaalid op en iemand van ons ondersteuningsteam maakt een aangepast abonnement voor u.

## Het aangepaste schema gebruiken {#use_custom}

In de toepassing `info.plist` Voeg de volgende code toe in het bestand:

```plist
    <key>CFBundleURLTypes</key>
    <array>
        <dict>
            <key>CFBundleURLSchemes</key>
            <array>
                <string>adbe.u-XFXJeTSDuJiIQs0HVRAg</string> // replace this with your custom scheme
            </array>
        </dict>
    </array>
```
