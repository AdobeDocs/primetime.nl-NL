---
title: Overzicht van het proces voor het verkrijgen van licenties
description: Overzicht van het proces voor het verkrijgen van licenties
copied-description: true
exl-id: 0e1c43a5-9a7d-4534-acd6-7feff94f4670
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Overzicht van het proces voor het verkrijgen van licenties{#license-acquisition-process-overview}

Het inschakelen van uw toepassing voor het afspelen van inhoud onder bescherming van Primetime DRM wordt in de volgende secties beschreven, met gebruik van ActionScript 3 (AS3)-codevoorbeelden. De nuanced afwijkingen van deze workflow voor native apps op mobiele platforms worden waar nodig weergegeven. De Primetime DRM-workflows zijn echter op alle platforms zeer vergelijkbaar, zodat u de AS3-code begrijpt en de extrapolatie naar andere platforms vrij eenvoudig maakt.

**Verwervingsproces licentie:**

1. Haal de DRM-metagegevens van de beveiligde inhoud op.
1. Controleren of een licentie lokaal beschikbaar is:

   * Als de licentie lokaal beschikbaar is, laadt u de licentie en gaat u naar Stap 6.
   * Ga naar stap 3 als de licentie niet lokaal beschikbaar is.

1. Controleren of verificatie vereist is:

   * Als verificatie vereist is, vraagt u de verificatiereferenties op van de gebruiker en geeft u deze door aan de licentieserver.
   * Als de authentificatie niet wordt vereist, ga naar Stap 6.

1. Als apparaatdomeinregistratie is vereist, sluit u zich aan bij het apparaatdomein.
1. Als de verificatie nodig was en nu is voltooid, downloadt u de licentie van de licentieserver.
1. Speel de inhoud af.

Als er geen fouten zijn opgetreden en de gebruiker is geautoriseerd om de inhoud weer te geven, verzendt Primetime een `DRMStatusEvent` en de toepassing begint met afspelen. De `DRMStatusEvent` -object bevat de gerelateerde licentiegegevens, die het beleid en de machtigingen van de gebruiker identificeert. Bijvoorbeeld: `DRMStatusEvent` kan informatie bevatten over de vraag of de inhoud offline toegankelijk kan worden gemaakt, wanneer de licentie verloopt, enzovoort.

De toepassing kan de licentiegegevens gebruiken om de gebruiker op de hoogte te stellen van de status van zijn beleid. De toepassing kan bijvoorbeeld het aantal resterende dagen dat de gebruiker heeft om de inhoud weer te geven, weergeven in een statusbalk. Als de gebruiker offline toegang heeft, wordt de licentie in de cache geplaatst en wordt de gecodeerde inhoud gedownload naar de computer van de gebruiker. De inhoud is toegankelijk voor de duur die is gedefinieerd in de duur van de licentiecache. De eigenschap detail in de gebeurtenis bevat `DRM.voucherObtained`. De toepassing bepaalt waar de inhoud lokaal wordt opgeslagen om deze offline beschikbaar te maken. U kunt licenties ook vooraf laden met de `DRMManager` klasse.
