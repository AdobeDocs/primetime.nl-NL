---
description: 'null'
seo-description: 'null'
seo-title: Lijst van afgewezen personen van DRM-clients die geen toegang hebben tot beveiligde inhoud
title: Lijst van afgewezen personen van DRM-clients die geen toegang hebben tot beveiligde inhoud
uuid: 38bc024e-0c5b-4c1c-8d4b-94b9e0fec67e
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Lijst van afgewezen personen van DRM-clients die geen toegang hebben tot beveiligde inhoud {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

Deze lijst van afgewezen personen geeft de Primetime DRM-clients aan die geen toegang hebben tot beveiligde inhoud. U lijst van afgewezen personen clients op clientversie en platform.

Voorbeeld van gebruik: In geval van een inbreuk op de beveiliging kan een nieuwere versie van de Primetime DRM-client worden opgegeven als de minimale versie die vereist is voor het aanschaffen van licenties en het afspelen van inhoud. De licentieserver controleert of de Primetime DRM-client die de licentieaanvraag indient, aan de versievereisten voldoet voordat een licentie wordt uitgegeven. De Primetime DRM-client controleert ook de versie in de licentie voordat de inhoud wordt afgespeeld. Deze clientcontrole is vereist in het geval van domeinen waar een licentie naar een andere computer kan worden overgedragen.

Een Primetime DRM-clientversie kan worden geïdentificeerd door de kenmerken die in de volgende tabel zijn opgegeven:

| **Kenmerk** | **Ondersteunde waarden** | **Criteria afstemmen** | **Beschrijving** |
|---|---|---|---|
| Omgeving | `“PC”, “PortingKit”` | Exacte overeenkomst | Geeft aan of de client op een desktopcomputer of op een ander apparaat wordt uitgevoerd. |
| OS | `“Win”, “Mac”, “Linux”, “Android”, “iOS”, "ChromeOS"` | Exacte overeenkomst | Platform |
| Architectuur | `“32”, “64”` | Exacte overeenkomst | 32-bits of 64-bits |
| Schermtype | `“PC”, “Mobile”, “TV”` | Exacte overeenkomst |  |
| Runtimeversie | Een geldig versienummer. Bijvoorbeeld, `“2.0.0”, "3.0", "4.0", "11.0"`enz. | Komt overeen met als de clientversie kleiner dan of gelijk is aan de opgegeven versie. | Versienummer is opgegeven als een combinatie van getallen en punten (&quot;.&quot;) van elke lengte. |
| Primetime DRM-bibliotheekversie | Een geldig versienummer. Bijvoorbeeld, `“2.0.0”`. | Komt overeen met als de clientversie kleiner dan of gelijk is aan de opgegeven versie. | Versienummer is opgegeven als een combinatie van getallen en punten (&quot;.&quot;) van elke lengte. |
| OEM-leverancier | De koord van de Leverancier van OEM dat in het Runtime Certificaat kan worden gevestigd dat aan een klant werd uitgegeven die Primetime DRM aan een apparaat steunde. | Exacte overeenkomst | De identificatiereeks van de Leverancier van OEM voor het apparaat gebruikend de het Porteren uitrusting. |
| Model | Modeltekenreeks die kan worden gevonden in het runtime-certificaat dat is uitgegeven aan een klant die Primetime DRM heeft geïmporteerd op een apparaat. Bijvoorbeeld: `"iOS_Mobile", "Android_Mobile", "Chrome", "ChromeOS_ARM", "WindowsOnARM", "AVE"` | Exacte overeenkomst | Identificatiereeks van het apparaatmodel voor het apparaat met behulp van de portkit. |

>[!NOTE]
>
>Wanneer u een item in de lijst van afgewezen personen opgeeft, kunt u waarden instellen voor een of meer van de kenmerken die in de vorige tabel worden genoemd. Elk kenmerk dat niet wordt opgegeven, wordt behandeld als een jokerteken. Als de Primetime DRM-client overeenkomt met alle waarden die in een lijst van afgewezen personen-item zijn opgegeven, heeft die client mogelijk geen toegang tot de beveiligde inhoud.

