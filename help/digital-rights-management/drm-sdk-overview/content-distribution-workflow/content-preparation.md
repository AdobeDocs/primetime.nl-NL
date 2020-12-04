---
description: Elk gebruik van Adobe Primetime DRM bestaat uit twee belangrijke stappen op verschillende punten van de workflow. De inhoud moet één keer per element worden voorbereid en dit leidt tot het maken van beveiligde inhoud. Inhoud aanschaffen wordt meerdere keren uitgevoerd, voor elke consument die dat beveiligde middel wil bekijken.
seo-description: Elk gebruik van Adobe Primetime DRM bestaat uit twee belangrijke stappen op verschillende punten van de workflow. De inhoud moet één keer per element worden voorbereid en dit leidt tot het maken van beveiligde inhoud. Inhoud aanschaffen wordt meerdere keren uitgevoerd, voor elke consument die dat beveiligde middel wil bekijken.
seo-title: Inhoud voorbereiden
title: Inhoud voorbereiden
uuid: edb633f0-b623-41ea-a52a-19017d45fb18
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Inhoudsvoorbereiding{#content-preparation}

Elk gebruik van Adobe Primetime DRM bestaat uit twee belangrijke stappen op verschillende punten van de workflow. De inhoud moet één keer per element worden voorbereid en dit leidt tot het maken van beveiligde inhoud. Inhoud aanschaffen wordt meerdere keren uitgevoerd, voor elke consument die dat beveiligde middel wil bekijken.

Voordat u inhoud beschikbaar maakt voor distributie, moet u eerst de inhoud in uw video-indeling coderen, een of meer beleidsregels maken die gebruiksregels voor de inhoud opgeven en de inhoud verpakken met gebruik van Adobe Primetime DRM SDK.

De stappen voor het coderen, verpakken en distribueren van inhoud zijn als volgt:

1. Codeer de inhoud in uw gewenste video-indeling met gebruik van coderingsgereedschappen die beschikbaar zijn bij Adobe of van derden.
1. Beleid maken waarin de gebruiksregels worden gespecificeerd waaronder consumenten de inhoud kunnen bekijken.

   Een beleid is de container voor de regels en beperkingen die bepalen hoe, wanneer en waar de beschermde inhoud door consumenten kan worden bekeken.

   De verpakker vereist minstens één beleid met minstens één gebruiksregel. U kunt de gebruiksregel overschrijven en aanvullende gebruiksregels toevoegen wanneer de licentieserver de licentie genereert.

1. Verpak de inhoud en geef op welk beleid u wilt toepassen.

   Primetime DRM SDK codeert de inhoud met behulp van een Content Encryption Key (CEK) en bindt een of meer beleidsregels aan de inhoud. Het resultaat is een *protected inhoudsbestand *dat alleen kan worden afgespeeld door een consument die een licentie heeft verkregen van de overeenkomstige licentieserver.

   Tijdens het verpakken wordt de inhoud versleuteld met behulp van de CEK. De CEK wordt gecodeerd met de openbare sleutel van de Server van de Vergunning en omvat in de meta-gegevens van Primetime DRM samen met het beleid. De DRM-metagegevens van Primetime worden ondertekend met de persoonlijke sleutel van Packager en de metagegevens worden opgenomen in de beveiligde inhoud.

1. De beschermde inhoud beschikbaar stellen voor distributie aan consumenten.

   De beveiligde inhoud wordt doorgaans gedistribueerd via een inhoudsdistributienetwerk (CDN). CDN kan om het even welk mechanisme gebruiken dat door cliëntruntime, zoals Flash Media Server, Adobe HTTP Dynamic Streaming voor veelvoudige bitrate het stromen, of een Server van het Web van HTTP voor progressieve download wordt gesteund.

