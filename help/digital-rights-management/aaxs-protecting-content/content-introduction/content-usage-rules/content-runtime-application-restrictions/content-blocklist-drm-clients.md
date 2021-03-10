---
title: Lijst van gewezen personen van DRM-clients die geen toegang hebben tot beveiligde inhoud
description: Lijst van gewezen personen van DRM-clients die geen toegang hebben tot beveiligde inhoud
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Lijst van gewezen personen van DRM-clients die toegang hebben tot beveiligde inhoud {#blocklist-of-drm-clients-restricted-from-accessing-protected-content}

**Adobe Access DRM-moduleversies hebben geen toegang tot beveiligde inhoud.**

Hiermee geeft u de DRM-client op die geen toegang heeft tot inhoud. Specified by DRM client version and platform.

Voorbeeld van gebruik: In geval van een inbreuk op de beveiliging kan een nieuwere versie van de DRM-client worden opgegeven als de minimale versie die vereist is voor het aanschaffen van licenties en het afspelen van inhoud. De licentieserver controleert of de DRM-client die de licentieaanvraag indient, aan de versievereisten voldoet voordat een licentie wordt uitgegeven. De DRM-client controleert ook de DRM-versie in de licentie voordat de inhoud wordt afgespeeld. Deze clientcontrole is vereist in het geval van domeinen waar een licentie naar een andere computer kan worden overgedragen.

Een DRM-clientversie kan worden geïdentificeerd aan de hand van de kenmerken die in de volgende tabel zijn opgegeven:

| **Kenmerk** | **Ondersteunde waarden** | **Criteria afstemmen** | **Beschrijving** |
|---|---|---|---|
| Omgeving | &quot;PC&quot;, &quot;PortingKit&quot; | Exacte overeenkomst | Geeft aan of de client op een desktopcomputer of op een ander apparaat wordt uitgevoerd. |
| OS | &quot;Win&quot;, &quot;Mac&quot;, &quot;Linux&quot;, &quot;Android&quot;, &quot;iOS&quot;, &quot;ChromeOS&quot; | Exacte overeenkomst | Platform |
| Architectuur | &quot;32&quot;, &quot;64&quot; | Exacte overeenkomst | 32-bits of 64-bits |
| Schermtype | &quot;PC&quot;, &quot;Mobile&quot;, &quot;TV&quot; | Exacte overeenkomst |  |
| Runtimeversie | Een geldig versienummer. Bijvoorbeeld &quot;2.0.0&quot;, &quot;3.0&quot;, &quot;4.0&quot;, &quot;11.0&quot;, enz. | Komt overeen met als de clientversie kleiner dan of gelijk is aan de opgegeven versie. | Versienummer is opgegeven als een combinatie van getallen en punten (&quot;.&quot;) van elke lengte. |
| DRM-bibliotheekversie | Een geldig versienummer. Bijvoorbeeld &quot;2.0.0&quot;. | Komt overeen met als de clientversie kleiner dan of gelijk is aan de opgegeven versie. | Versienummer is opgegeven als een combinatie van getallen en punten (&quot;.&quot;) van elke lengte. |
| OEM-leverancier | Tekenreeks OEM-leverancier | Exacte overeenkomst | De identificatiereeks van de Leverancier van OEM voor het apparaat gebruikend de het Porteren uitrusting. |
| Model | Modeltekenreeks. Bijvoorbeeld &quot;iOS_Mobile&quot;, &quot;Android_Mobile&quot;, &quot;Chrome&quot;, &quot;ChromeOS_ARM&quot;, &quot;WindowsOnARM&quot;, &quot;AVE&quot; | Exacte overeenkomst | Identificatiereeks van het apparaatmodel voor het apparaat met behulp van de portkit. |

>[!NOTE]
>
>Wanneer u een item in de lijst van gewezen personen opgeeft, kunnen waarden worden ingesteld voor een of meer van de kenmerken die in de vorige tabel worden genoemd. Elk kenmerk dat niet wordt opgegeven, wordt behandeld als een jokerteken. Als de DRM-client overeenkomt met alle waarden die in een lijst van gewezen personen-item zijn opgegeven, heeft die client mogelijk geen toegang tot de beveiligde inhoud.

